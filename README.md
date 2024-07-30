## linux-6.6.43-config

1. 원하는 버전의 커널 다운받기 (kernel.org에서 tar 파일로 다운 또는 github에서 원하는 태그 다운)
  a. Makefile의 extraversion을 수정하여 kernel version 이름을 커스텀 할 수 있음 (ex. linux-6.6.10.erb)
2. .config 파일 생성 (최신 버전 커널을 다운 받는데 config는 너무 옛날 버전을 사용하는 경우 등 config를 잘못 생성하면 커널이 망가짐. )
  a. sudo cp -v /boot/config-5.15 .config
  b. 위 명령어는 boot directory에 이미 존재하는 다른 .config 파일을 내 kernel .config 파일로 복사하는 명령어.
  c. sudo cp -v (복사 할 config 파일 위치) (생성 될 config 파일 위치)
3. sudo make menuconfig
  a. load -> exit
4. sudo make bzImage
5. sudo make modules
   a. 3,4,5번 명령어는 시간이 오래 걸리므로 빠르게 끝내고 싶으면 -j (원하는 core 개수) 옵션을 줘서 여러개의 core를 사용해 컴파일 가능
   b. ex) sudo make bzImage -j 96
7. sudo make modules_install
   a.  grub 상태를 update 하는 것 /etc/default/grub 에 변경이 있을 경우 update를 해줘야 원하는 커널로 부팅 됨.
8. sudo make install
9. sudo update-grub
10. sudo reboot
