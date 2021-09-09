
## 说明

1. 项目克隆自[简易云音乐](https://github.com/dufu1991/simple-cloud-music/)，详细信息请移步；
2. 部分内容有修改和添加，主要是为了适应个人服务器环境。
3. demo页面请移步[简易云音乐](https://github.com/dufu1991/simple-cloud-music/)


## ⚙️ 部署

如果你有自己的服务器，建议将此应用与网易云 API 都部署至你自己的服务器，减轻我的服务器压力。

1. 部署网易云 API，详情参见 [Binaryify/NeteaseCloudMusicApi](https://github.com/Binaryify/NeteaseCloudMusicApi)。

2. 执行`git clone https://github.com/LeeRoJaN/simple-cloud-music.git`克隆本仓库代码。

3. 设备安装好 node 环境之后，进入工程目录，执行 `node i` 安装依赖。

4. 修改 `src/utils/request.js` 文件里面的 baseURL 为你的网易云 API 地址，执行 `npm run dev` 启动本地联调，此时访问的是 public 下面的文件。

5. 执行 `npm run build` 编译打包文件至 html 目录下，然后将 html 文件夹里面的文件上传到你的 Web 服务器即可访问。

6. 如果要直接部署，执行 `npm run deploy` 根据命令行提示输入自己的服务器地址、账号、密码、静态文件部署路径等信息，将直接将打包好的工程部署至 Web 服务器。

7. 要实现 PWA 的 Service Workers（离线访问），必须要 HTTPS 证书，关于域名、证书、服务器等相关内容请自行了解。

## 📜 开源许可

本项目仅供个人学习研究使用，禁止用于商业及非法用途。

基于 [MIT license](https://opensource.org/licenses/MIT) 许可进行开源。

## 🌊 感谢

非常感谢 API 源代码，来自 [Binaryify/NeteaseCloudMusicApi](https://github.com/Binaryify/NeteaseCloudMusicApi) 。

- [Apple Music](https://music.apple.com/)

- [Spotify](https://www.spotify.com/)

- [网易云音乐](https://music.163.com/)

- [YesPlayMusic](https://github.com/qier222/YesPlayMusic)

- [简易云音乐](https://github.com/dufu1991/simple-cloud-music/)


