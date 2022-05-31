# Prototype 1

Unity Learn の [Junior Programmer](https://learn.unity.com/pathway/junior-programmer) Pathway に含まれる Create with Code 1 の [Unit 1](https://learn.unity.com/project/unit-1-driving-simulation) に出てくる `Prototype 1` 用リポジトリ

![play image](https://play-static.unity.com/20220531/p/images/a2727b6b-6aeb-4db6-b218-995a95474cda_Pasted_Image_2022_06_01_7_07.png)

- [ここでプレイできるよ - play.unity.com](https://play.unity.com/mg/other/super-simple-driving-simulator)

## 必要な Asset

- Prototype 1 Starter Files に含まれる `Prototype-1_Starter-Files.unitypackage`
  - Starter Files と Asset Import 方法は[こちら](https://learn.unity.com/tutorial/set-up-your-first-project-in-unity#5cca0230edbc2a635ca5d6d2)を参照のこと

## WebGL 向けの Build ができない場合

macOS Monterey 12.3 以降で Python 2.7 が削除された
https://developer.apple.com/documentation/macos-release-notes/macos-12_3-release-notes

その影響で WebGL 向けの Build が失敗するようになった...

以下の Script を `Assets/Scripts/` に設置して `/path/to/your/python` を使っている環境に併せて更新すればまた Build できるようになるよ！

```csharp
#if UNITY_EDITOR
using UnityEditor.Build;
using UnityEditor.Build.Reporting;

public class WebGLPreBuildProcessing : IPreprocessBuildWithReport
{
    public int callbackOrder => 1;
    public void OnPreprocessBuild(BuildReport report)
    {
        System.Environment.SetEnvironmentVariable("EMSDK_PYTHON", "/path/to/your/python");
    }
}
#endif
```
