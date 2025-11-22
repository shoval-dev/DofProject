## 工具说明
DOF 客户端插件，具备多种扩展功能

## 安装与编译
> 依赖：  
> - [Visual Studio 2022](https://visualstudio.microsoft.com/zh-hans/downloads/)

0. 克隆本仓库
1. 安装好 **Visual Studio 2022**（勾选“使用 C++ 的桌面开发”工作负载）
2. 打开 **Developer Powershell for VS 2022**，切换到工程目录，例如：
   ```powershell
      cd path\to\DofProject-main
   ````

3. 运行编译命令（Debug / x86）：
   ```powershell
   msbuild .\DofProject.sln /m /t:Clean,Build "/p:Configuration=Debug;Platform=x86"
   msbuild .\DofProject.sln /m /t:Clean,Build "/p:Configuration=Release;Platform=x86"
   ```
4. 编译成功后，生成的插件位于 `Debug` 或 `Release`目录：
   * `Debug\DofProject.dll`（插件主体）
   * `Debug\DofProject.pdb`（调试符号）

   * `Release\DofProject.dll`（插件主体）
   * `Release\DofProject.pdb`（调试符号）

## 免责声明
* 本项目仅供学习与技术研究使用
* 使用本项目时，必须严格遵守当地法律法规
* 严禁任何形式的 **商业用途** 或破坏性用途，后果自负

## 其他说明
* `xini_file.h`、`Memory.h` 由 **[MUQING-](https://tieba.baidu.com/home/main?id=tb.1.cc1a8da3.n9QsE8gyyuSLD6Lb_SQUIg)** 大佬分享自用
* 工程仅供 **C++ 写法参考 / 学习用例**，不保证在所有客户端环境中的稳定性

## 自定义功能开关（配置示例）
> DLL 加载成功后，默认会在同目录生成 `dof.ini` 配置文件（部分功能默认关闭，主要针对 0627 版本）

// 初始化配置文件读写类
xini_file_t xini_file(config_file);

// 系统配置
xini_file["系统配置"]["服务器IP"]      = "192.168.200.131";
xini_file["系统配置"]["客户端版本"]    = version;
xini_file["系统配置"]["本地日志"]      = 0;
xini_file["系统配置"]["HOOK聊天消息"]  = 0;

// 功能配置
xini_file["功能配置"]["本地GM"]              = 0; // 建议关闭
xini_file["功能配置"]["装备镶嵌"]            = 0;
xini_file["功能配置"]["文本粘贴权限"]        = 1;
xini_file["功能配置"]["邮件GM标识"]          = 1;
xini_file["功能配置"]["关闭回购商店"]        = 1;
xini_file["功能配置"]["技能栏显示技能名称"]  = 0;
xini_file["功能配置"]["修复233包头"]         = 1;
xini_file["功能配置"]["修复移动物品"]        = 1;
xini_file["功能配置"]["修复字母显示"]        = 1;
xini_file["功能配置"]["禁用最小化其他窗口"]  = 0;
xini_file["功能配置"]["缩放优化"]            = 0;
xini_file["功能配置"]["修复领主之塔"]        = 1;
xini_file["功能配置"]["修复二觉名称乱码"]    = 0;
xini_file["功能配置"]["默认创建缔造者"]      = 0;

// 颜色配置
xini_file["颜色配置"]["启用"]          = 0;
xini_file["颜色配置"]["角色名称颜色"]  = "#FFFFFF";
xini_file["颜色配置"]["NPC名称颜色"]   = "#E6C89B"; // Hook

// 键位配置
xini_file["键位配置"]["启用"]     = 0;
xini_file["键位配置"]["HookKey1"] = 55;  // Hook 菜单 ID
xini_file["键位配置"]["1键X轴"]   = 718;
xini_file["键位配置"]["1键Y轴"]   = 520;
xini_file["键位配置"]["HookKey2"] = 56;  // Hook 菜单 ID
xini_file["键位配置"]["2键X轴"]   = 718;
xini_file["键位配置"]["2键Y轴"]   = 558;

## 已知问题
* “本地 GM” 功能开启后，游戏启动崩溃几率较高，**强烈建议保持关闭**（默认配置中为 `0`）

## 更新日志

* 历史更新记录请查看：`CHANGELOG.md`