# ESLint相关问题

- 比如说在vue的脚手架当中，创建项目模板的时候选择eslint插件，这时候会有个cli-plugin-eslint这个插件被安装，这个插件有默认的eslint配置，在整个webpack的生命周期内，这个插件的eslint配置影响着所有相关的js、vue文件等。
- 当我们配置了 .eslintrc 文件之后，我们可以自定义一些rules
- 假设 我删除  .eslintrc 或者 破坏  .eslintrc 的结构，这时候 .eslintrc 不是个有效的配置文件，这时候整个脚手架不会提示你配置文件不可用或者出错了，而是不会加载这个 .eslintrc 配置文件。此时生效的应该是 cli-plugin-eslint 这个插件的默认配置。（待验证）
- 有时候我们更改了 .eslintrc 的配置后，代码检测没有立即生效，就是 node_modules 文件夹下的 .cache 文件夹 导致的，删除这个缓存文件即可即时生效。