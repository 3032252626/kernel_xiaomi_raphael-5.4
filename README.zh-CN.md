# 红米 K20 Pro (raphael) 5.4 GKI 内核

## 简介

本仓库是 [HeliumStudio-Dev/kernel_xiaomi_raphael-5.4](https://github.com/HeliumStudio-Dev/kernel_xiaomi_raphael-5.4) 的镜像 fork，用于配合 GitHub Actions 自动化编译带 LXC/Docker + KernelSU 的内核包。

- **设备**: Redmi K20 Pro / K20 Pro Premium (raphael, 骁龙855 sm8150)
- **内核版本**: Linux 5.4.302 GKI (Generic Kernel Image)
- **分支**: `zundamon-miui-5.4`
- **LocalVersion**: `-Zundamon-NEXT-v1.0-alpha3`
- **适配 ROM**: KameYuki HyperOS 4 (Android 16/17)

## 已有配置

- `CONFIG_KPROBES=y` — KernelSU hook 依赖
- `CONFIG_MODULES=y` / `CONFIG_MODVERSIONS=y` — 模块支持
- `CONFIG_KSU_HACK_ARM64_BRANCH_LINK=y` — KSU ARM64 分支链接补丁
- `CONFIG_KSU_THRONE_TRACKER_ALWAYS_THREADED=y`
- defconfig: `arch/arm64/configs/raphael_defconfig`

## 已知 Bug

- MTP（USB 文件传输）不可用
- 快充不生效
- 视频录制异常
- 待机耗电偏高

## 编译

通过 [LXC-DOCKER-KernelSU_for_k20pro](https://github.com/3032252626/LXC-DOCKER-KernelSU_for_k20pro) 仓库的 GitHub Actions 工作流编译：

- `build-AB-Mandi-Sa.yml` — Mandi-Sa clang 22
- `build-AB-zyc.yml` — zyc clang 18

编译产物通过 AnyKernel3 打包为 zip，TWRP 刷入。

## 致谢

- [HeliumStudio-Dev](https://github.com/HeliumStudio-Dev) — 原始内核源码
- [tiann](https://github.com/tiann) — KernelSU
- [ravindu644](https://github.com/ravindu644/Droidspaces-OSS) — Droidspaces 内核补丁
- [fate-think](https://github.com/fate-think/LXC-DOCKER-KernelSU_Action) — LXC/Docker 配置脚本
