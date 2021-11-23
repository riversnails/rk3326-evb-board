# rk3326-evb-lp10-board
rk3326 evb보드의 펌웨어를 만들어 봤습니다.

소스코드를 repo명령어로 받아와야 하는데 새 폴더를 만든 뒤

repo init --repo-url=https://github.com/rockchip-linux/repo --no-clone-bundle -u https://github.com/rockchip-linux/manifests -b master

명령어를 입력한다. 이게 rk에서 만든 것이 문제인지 repo를 init하는데 python을 2.7  3.7 바꿔가며 설치해야
한다. 이때 정상적인 방법으로 리눅스에 python의 버전들이 깔려있다면

sudo update-alternatives --config python

명령어로 버전들을 바꿀 수 있다.
이렇게 설치를 하면 바로 sync를 하는 것이 아니라 rk3326_linux.xml을 .repo/manifests 폴더에 넣은 후,

repo init --repo-url=https://github.com/rockchip-linux/repo --no-clone-bundle -u https://github.com/rockchip-linux/manifests -b master -m rk3326_linux.xml

명령어로 rk3326보드를 타겟으로 설정 해 준다.
바로 px30을 타겟으로 잡고 다운해도 상관 없지만 그럴 경우 보드 설정에서 직접 찾아 설정해줘야 한다.

repo sync --no-clone-bundle

로 repo를 다운받는다.
다운이 끝난다면 build.sh파일이 보일 것이다. 처음 실행하게 된다면 타겟보드를 선택하라고 나올 것이다.
이 보드는 자신의 보드에 맞춰 설정해주면 된다.
다시 명령어에 help를 해본다면 많은 옵션들이 나온다. 잘 모르겠다면 allsave를 넣고 돌리면 될 것이다.



##buildroot에서 deviceio부근에서 막히는 문제
막힌 뒤 buildroot로 이동해준다. 그 후
package/rockchip/deviceio_release/deviceio_release.mk
파일을 덮어씌워준다.


참고 사이트들:
https://github.com/rockchip-linux/manifests
http://opensource.rock-chips.com/wiki_Main_Page
https://aciddust.github.io/blog/post/Firefly-RK3399-%EA%B0%9C%EB%B0%9C%ED%99%98%EA%B2%BD-%EA%B5%AC%EC%B6%95/#%EB%81%9D
