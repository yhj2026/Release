# ServoWorks / WinSFTune 在线更新资料

仓库：https://github.com/yhj2026/Release

## 文件说明

| 文件 | 说明 |
|------|------|
| `version.json` | 版本清单（客户端固定读取） |
| GitHub **Releases** 附件 | 安装包 zip（不要把大 zip 长期塞进 git 仓库） |

## version.json 字段

```json
{
  "version": "50000029",
  "url": "https://github.com/yhj2026/Release/releases/download/v50000029/ServoWorks_50000029.zip",
  "sha256": "小写十六进制，可先留空（不校验）",
  "changelog": "更新说明"
}
```

客户端读取地址：

`https://raw.githubusercontent.com/yhj2026/Release/main/version.json`

## 发布新版本步骤

1. 把完整可运行目录打成 zip（根目录需含 `ServoWorks.exe` 及依赖 dll；建议不要覆盖正在运行的 `MaintenanceTool.exe`，或接受该文件更新失败）。
2. 在 GitHub 建 Release，Tag 例如 `v50000029`，上传 `ServoWorksPatch50000029.zip`。
3. 修改本仓库 `version.json`：`version` / `url` / `changelog`，建议填 `sha256`。
4. `git add version.json && git commit && git push`
5. 客户端 `SOFTVERSION_NUMBER` 发版时改为同一新版本号。

## 计算 sha256（PowerShell）

```powershell
Get-FileHash .\ServoWorksPatch50000029.zip -Algorithm SHA256
```

把输出的 Hash 填进 `version.json`（小写或大写均可，客户端按不区分大小写比较）。
