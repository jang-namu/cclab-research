# Operating System

## File and File System
* File: 연관된 정보를 이름을 가지고 저장.
    * 일반적으로 비휘발성 보조기억장치에 저장 
    * 운영체제는 다양한 저장장치를 file이라는 동일한 논리적 단위로 볼 수 있게 해준다.
    * Operation
        * create, read, write, reposition(lseek), delete, open, close 등

* File attribute(metadata)
    * 파일 자체의 내용이 아니라 파일을 관리하기 위한 각종 정보들
    * 파일 이름, 유형, 저장된 위치, 파일 사이즈
    * 접근 권한 (read, write, execute), 시간 (생성/변경/사용), 소유자 등

* File system
    * 운영체제에서 파일을 관리하는 부분
    * 파일 및 파일의 메타데이터, 디렉토리 정보 등을 관리
    * 파일의 저장 방법 결정, 파일 보호

* Directory
    * 파일의 메타데이터 중 일부를 보관하고 있는 특별한 파일
    * 그 디렉토리에 속한 파일 이름 및 파일 메타데이터들
    * operation
        * search for a file, create fa file, delete a file
        * list a direcotry, rename a file, traverse the file system(파일 시스템 전체를 탐색)

* Partition (= Logical Disk)
    * 운영체제는 논리적인 디스크를 본다. 하나의 (물리적)디스크 안에 여러 파티션을 두는게 일반적
    * 여러개의 물리 디스크를 하나의 파티션으로 구성하기도 함
    * (물리) 디스크를 파티션으로 구성한 뒤 각각 파티션에 file system을 깔거나 swapping 등 다른 용도로 사용할 수 있다.

* open(): **파일의 메타데이터를 디스크 -> 메인 메모리로 올려놓는다.**
    * open("/a/b/c"): 디스크로부터 파일 c의 메타데이터를 메모리를 가지고 옴
    * 이미 알려진 루트디렉토리부터 따라 내려가며 찾는다.
    1. root의 metadata를 먼저 연다.(Open File table) -> root의 content를 확인해서 a의 메타데이터를 찾는다.
    2. a의 메타데이터를 PCB Open file table에 올려 연다. -> b의 content를 확인해서 b의 메타데이터를 찾는다.
    3. b의 메타데이터를 PCB에 올린다.
    4. System Call의 결과값으로 파일 b의 메타데이터를 가리키는 file descripter를 반환한다.
        * file descripter는 Open file table에 있는 b의 메타데이터를 가리킬 것이다.
        ```
        #if system call이 다음과 같으면?
        fd = open("/a/b")
        read(fd)
        ```
    * b의 내용을 시작위치부터 읽어올 것이다. 운영체제가 자신의 메모리 공간 일부에 데이터를 먼저 읽어놓는다.(buffer cash)
    * 그 후 이를 copy해서 사용자 메모리 영역에 전달한다. 다시 한 번 같은 내용을 요청하게 되면 캐싱되어있는 데이터를 사용한다.
    