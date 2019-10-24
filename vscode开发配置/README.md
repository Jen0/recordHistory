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
3. `vscode-js-import` 配置自动引入，同时可以配置别名路径的引入
   ```json
    "js-import.root": "src",
    "js-import.alias": {
        "@": "src/",
        "@/utils": "src/utils",
    },
    // 扫描排除文件
    "js-import.excludeFilesToScan": "**/dist/**",
   ```
   输入方法名，自动导入效果：
   ```js
   import { method } from '@/utils/common';
   ```
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

