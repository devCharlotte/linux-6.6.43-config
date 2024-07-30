## linux-6.6.43-config
 </br>
- 원하는 버전의 커널 다운 받고 압축 해제 (kernel.org에서 tar 파일로 다운 or github에서 원하는 태그 다운) </br>
 - Makefile의 extraversion을 수정하여 kernel version 이름 커스텀 가능 </br>
- .config 파일 생성 (최신 버전 커널을 다운 받는데 config이 아주 예전 버전이거나 config를 잘못 생성하면 커널 고장) </br>
 - sudo cp -v /boot/config-5.15.116-genetic .config </br>
 - 위 명령어는 boot directory에 이미 존재하는 다른 .config 파일을 내 kernel .config 파일로 복사하는 명령어. </br>
 - sudo cp -v (복사 할 config 파일 위치) (생성 될 config 파일 위치) </br>
- sudo make menuconfig </br>
 - load -> exit 가져온 config 파일로 로딩할 수 있음 </br>
- sudo make bzImage </br>
- sudo make modules </br>
 - 3,4,5번 명령어는 시간이 오래 걸림.  -j (원하는 core 개수) 옵션을 줘서 여러 개의 core로 컴파일하면 속도 업 </br>
 - ex) sudo make bzImage -j 128 </br>
- sudo make modules_install </br>
 - grub 상태를 update 하는 것 /etc/default/grub 에 변경이 있을 경우 update를 해야 원하는 커널로 부팅 가능 </br>
- sudo make install </br>
- sudo update-grub </br>
- sudo reboot </br>
