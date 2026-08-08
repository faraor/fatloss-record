减脂记录｜iPhone PWA 安装说明

这不是“文件 App 里直接打开的 HTML”，而是一个可安装到 iPhone 主屏幕的 PWA。

一、为什么要这样用
- PWA 需要通过 HTTPS 地址打开。
- 安装后从桌面图标启动，会以独立 App 形式显示，不出现 Safari 地址栏。
- 59 条历史体重 + 4 组历史围度已经内置。
- 新数据优先保存在 IndexedDB。
- Service Worker 会缓存应用页面，因此首次联网打开后可离线使用。

二、部署
把整个“减脂记录_iPhone_PWA”文件夹原样上传到任意静态 HTTPS 托管服务。
必须保留：
- index.html
- manifest.webmanifest
- sw.js
- icons/ 文件夹

不要只上传 index.html，否则无法安装为完整 PWA，也无法离线缓存。

三、iPhone 安装
1. 在 iPhone 上使用 Safari 打开部署后的 HTTPS 地址。
2. 点 Safari 的“分享”按钮。
3. 选择“添加到主屏幕”。
4. 名称保持“减脂记录”，点击添加。
5. 以后从桌面“减脂记录”图标进入，不要再从“文件”App打开 HTML。

四、数据
- 历史数据已经写入应用。
- 新增/修改记录会保存到浏览器的 IndexedDB。
- 右上角“•••”可以导出 JSON 备份。
- 换手机、清除 Safari 网站数据或重装前，建议先导出备份。
- 如果系统阻止持久化数据库，App 顶部会显示提示。

五、更新
如果以后拿到新版文件：
1. 用新版文件覆盖服务器上的旧文件。
2. 把 sw.js 里的 CACHE_NAME 改成新版本号，例如 v2、v3。
3. 再打开一次 App，缓存会更新。
