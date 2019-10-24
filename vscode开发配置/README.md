- [vscode提升开发效率的配置（VUE版）](#vscode%e6%8f%90%e5%8d%87%e5%bc%80%e5%8f%91%e6%95%88%e7%8e%87%e7%9a%84%e9%85%8d%e7%bd%aevue%e7%89%88)
    - [路劲相关的插件及其使用](#%e8%b7%af%e5%8a%b2%e7%9b%b8%e5%85%b3%e7%9a%84%e6%8f%92%e4%bb%b6%e5%8f%8a%e5%85%b6%e4%bd%bf%e7%94%a8)

# vscode提升开发效率的配置（VUE版）

> 推荐插件

### 路劲相关的插件及其使用
1. `Path Intellisense` 文件路径提示
2. `path-alias` 配置别名后，可以从带有别名的路径中直接跳转定义
    ```json
    "pathAlias.aliasMap": {
        "@": "${cwd}/src"
    }
    ```
3. `vscode-js-import` 配置自动引入，同时，
   * 可以配置别名路径的引入
   * 快捷键`ctrl+alt+H`选择引入文件
   * 可以自动引入export default 
   ```json
    "js-import.root": "src",
    "js-import.alias": {
        "@": "src/",
        "@/utils": "src/utils",
    },
    //扫描文件
    "js-import.filesToScan": "**/*.{jsx,js,tsx,ts,vue}",
    //扫描排除文件
    "js-import.excludeFilesToScan": "**/dist/**", 
    //import default 后缀
    "js-import.plainFileSuffixWithDefaultMember": "json,js,vue", 
   ```
   输入方法名，自动导入效果：
   ```js
   import { method } from '@/utils/common';
   ```
   ![vscode-js-import插件](https://jeno.oss-cn-shanghai.aliyuncs.com/web/vscode/auto_import.gif)
4. 在根目录添加配置`jsconfig.js`文件，
   * 可以实现别名引入的**方法**的定义**跳转**，
   * 可以实现使用别名引入组件
   ```json
    {
        "compilerOptions": {
            "target": "ES6",
            "module": "commonjs",
            "allowSyntheticDefaultImports": true,
            "baseUrl": "./",
            "paths": {
                "@/*": ["src/*"]
            }
        },
        "exclude": ["node_modules"]
    }
   ```

