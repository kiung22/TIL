# Unity WebGL

- C# 코드로 작성된 script를 WebAssembly로 변환해준다.

- WebGL로 빌드할 경우에는 플랫폼의 한계때문에 Unity의 모든 기능을 사용할 수는 없다.
- 참고: [Unity WebGL document](https://docs.unity3d.com/kr/current/Manual/webgl-gettingstarted.html)



### How to publish for WebGL

1. **File** > **Build Settings**에서 **WebGL**을 선택하고 **Switch Platform**을 클릭한다.

2. **Add Open Scene**버튼을 눌러 프로젝트의 씬을 추가한다.

3. output setting을 수정하기 위해 **Edit** > **Project Settings**에서  **Player Settings**를 선택하고 Company Name, Product Name, Version 값을 입력한다. 다른 output settings도 수정을 할 수 있다.

   ![image-20210801154909052](Unity WebGL.assets/image-20210801154909052.png)

4. 설정이 끝나면 다시 **File** > **Build Settings** 창에서 **Build**를 눌러 build하거나 **Build And Run**을 눌러 build 후 자동으로 웹 브라우저로 실행시킬 수 있다. build 파일은 기본적으로 gzip으로 압축된 상태로 생성이 되지만 Unity에는 JavaScript로 작성된 압축 풀기 소프트웨어가 들어 있어서 작동하는 데에는 아무런 문제가 없다.

   ![image-20210801155520160](Unity WebGL.assets/image-20210801155520160.png)

- 참고: [Unity WebGL tutorial](https://learn.unity.com/tutorial/how-to-publish-for-webgl-2019-3?uv=2020.2#6050b6b4edbc2a39030af55f)

