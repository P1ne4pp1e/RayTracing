# RayTracing

RayTracing 是从《Ray Tracing in One Weekend》第一册的最终示例源码提取并整理的独立 C++ 学习项目。光线追踪的核心实现来自上游。

## 来源与许可

- 原作品《Ray Tracing in One Weekend》由 Peter Shirley、Trevor David Black 和 Steve Hollasch 署名。这里使用的提交对应正文 v4.0.2。[第一册在线正文](https://raytracing.github.io/books/RayTracingInOneWeekend.html) · [该提交中的第一册正文](https://github.com/RayTracing/raytracing.github.io/blob/0ab7db4c08fe23f23c0d9d30fed166c83cefed91/books/RayTracingInOneWeekend.html)
- 上游项目由 GitHub 的 RayTracing 组织维护，Steve Hollasch 是 v4.0.2 的发布者，也是贡献指南列出的项目联络人。[上游仓库](https://github.com/RayTracing/raytracing.github.io) · [上游发布页](https://github.com/RayTracing/raytracing.github.io/releases/tag/v4.0.2) · [上游贡献指南](https://github.com/RayTracing/raytracing.github.io/blob/0ab7db4c08fe23f23c0d9d30fed166c83cefed91/CONTRIBUTING.md#questions)
- 源码提取自上游 `release` 分支的提交 `0ab7db4c08fe23f23c0d9d30fed166c83cefed91`。[固定提交的第一册源码目录](https://github.com/RayTracing/raytracing.github.io/tree/0ab7db4c08fe23f23c0d9d30fed166c83cefed91/src/InOneWeekend)
- 上游示例代码采用 CC0 1.0 Universal。源码中的原作者声明和 CC0 声明均完整保留。[本地 COPYING.txt](COPYING.txt) · [上游 COPYING.txt](https://github.com/RayTracing/raytracing.github.io/blob/0ab7db4c08fe23f23c0d9d30fed166c83cefed91/COPYING.txt)

## 本地整理

第一册源码按职责分目录，项目配置精简为一个 CMake 可执行目标，并附上中文说明和生成文件的 Git 忽略规则。源码中的差异仅为双引号 `#include` 路径统一改为相对于 `src/` 的路径，包含顺序与上游一致。

| 位置 | 职责 |
| --- | --- |
| `src/main.cc` | 程序入口，组装场景与相机参数并启动渲染 |
| `src/core/` | 向量、光线、数值区间和通用工具 |
| `src/geometry/` | 求交接口、物体集合和球体 |
| `src/materials/` | 材质及光线散射 |
| `src/rendering/` | 相机、采样和 PPM 颜色输出 |

## 构建与运行

需要 CMake 3.15 或更新版本、支持 C++11 的编译器，以及对应 CMake 生成器的构建工具。项目只使用 C++ 标准库，可直接在项目根目录构建。

以下命令已在 Windows 上使用 CMake 4.2.0、MinGW-w64 GCC 14.2.0 和 `mingw32-make` 验证。请确保这些工具可从 `PATH` 找到。

```powershell
cmake -S . -B build -G "MinGW Makefiles" -DCMAKE_BUILD_TYPE=Release
cmake --build build --parallel
cmd /c '.\build\RayTracing.exe > build\image.ppm 2> build\render.log'
```

程序将 ASCII PPM（`P3`）写入标准输出，将渲染进度写入标准错误。上面的命令使用 `cmd` 重定向，在 `build/` 中生成 `image.ppm` 和 `render.log`。默认图像为 1200 × 675 像素，每像素 10 个样本，可用支持 PPM 的图像查看器打开。
