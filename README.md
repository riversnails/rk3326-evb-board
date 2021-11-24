# rk3326-evb-board
rk3326 evb보드의 펌웨어를 만들어 봤습니다.

-------

소스코드를 repo명령어로 받아와야 하는데 새 폴더를 만든 뒤

<pre>
<code>
repo init --no-clone-bundle -u https://github.com/rockchip-linux/manifests -b master
</code>
</pre>

명령어를 입력한다.
원래는 

<pre>
<code>
--repo-url=https://github.com/rockchip-linux/repo 
</code>
</pre>

인수가 있었는데 기존의 repo랑 충돌이 있어 사용하지 않는다.


이 후 sync를 하는 것이 아니라 rk3326_linux.xml을 .repo/manifests 폴더에 넣은 후,

<pre>
<code>
repo init --repo-url=https://github.com/rockchip-linux/repo --no-clone-bundle -u https://github.com/rockchip-linux/manifests -b master -m rk3326_linux.xml
</code>
</pre>

명령어로 rk3326보드를 타겟으로 설정 해 준다.
바로 px30을 타겟으로 잡고 다운해도 상관 없지만 그럴 경우 보드 설정에서 직접 찾아 설정해줘야 한다.

<pre>
<code>
repo sync --no-clone-bundle
</code>
</pre>

위 명령어로 repo를 다운받는다.
다운이 끝난다면 build.sh파일이 보일 것이다. 처음 실행하게 된다면 타겟보드를 선택하라고 나올 것이다.
이 보드는 자신의 보드에 맞춰 설정해주면 된다.
다시 명령어에 help를 해본다면 많은 옵션들이 나온다. 잘 모르겠다면 allsave를 넣고 돌리면 될 것이다.



### buildroot에서 deviceio부근에서 막히는 문제
막힌 뒤 buildroot로 이동해준다. 그 후
package/rockchip/deviceio_release/deviceio_release.mk
파일을 덮어씌워준다.

-------


참고 사이트들
https://github.com/rockchip-linux/manifests 
http://opensource.rock-chips.com/wiki_Main_Page 
https://aciddust.github.io/blog/post/Firefly-RK3399-%EA%B0%9C%EB%B0%9C%ED%99%98%EA%B2%BD-%EA%B5%AC%EC%B6%95/#%EB%81%9D
