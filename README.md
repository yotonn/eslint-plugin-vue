# ESLINT 使用说明书
本文主要介绍如何快速的在vscode中使用eslint的`eslint-plugin-vue`插件对Vue代码检查
- [关于eslint介绍](http://eslint.cn/docs/about/)
- [关于eslint-plugin-vue](https://github.com/vuejs/eslint-plugin-vue)
- [关于vscode介绍](https://code.visualstudio.com/)
- [关于Vue介绍](https://cn.vuejs.org/v2/guide/)

### 开始

1. 安装eslint,eslint-plugin-vue,babel-eslint

    首先你要确保本地环境中 `Node.js (>=4.x), npm version 2+`，推荐使用`yarn`代替`npm`，[关于yarn介绍](https://yarn.bootcss.com/)
    - eslint可以选择本地或者全局安装

        `yarn add eslint eslint-plugin-vue babel-eslint --dev`

        或者

        `npm install eslint eslint-plugin-vue babel-eslint --save-dev`

    关于eslint安装本地还是全局，[官方介绍](http://eslint.cn/docs/user-guide/getting-started)比较详细,解释起来就是说你的eslint和eslint-plugin-vue安装路径必须保持一致，要么全用本地安装，要么全用全局安装。

2. 配置文件

    我不太赞成使用`eslint --init`去生成一个`.eslintrc.*`的配置文件，因为这样你还是需要手动去修改配置，你可以直接在你的项目根目录下创建一个`.eslintrc.json`。
    
    下面是`.json`配置文件的内容你可以直接贴到你的配置文件里使用。

    ```json
    {
        "env": {
            "es6": true,
            "browser": true,
            "commonjs": true
        },
        "globals": {
            "Vue": true,
            "VueRouter": true,
            "iview": true
        },
        "extends": "plugin:vue/recommended",
        "parserOptions": {
            "parser": "babel-eslint",
            "ecmaVersion": 6,
            "sourceType": "module",
            "ecmaFeatures": {
                "jsx": false
            }
        },
        "plugins": [
            "vue"
        ],
        "rules": {
            "indent": [
                "error",
                4
            ],
            "linebreak-style": [
                "error",
                "unix"
            ],
            "quotes": [
                "error",
                "single"
            ],
            "semi": [
                "error",
                "never"
            ],
            "no-console": 1,
            "comma-dangle": ["error", "never"],
            "vue/html-indent": [2, 4],
            "vue/max-attributes-per-line": [2, {
                "singleline": 10,
                "multiline": {
                    "max": 10,
                    "allowFirstLine": true
                }
            }],
            "vue/no-parsing-error": [2, {
                "x-invalid-end-tag": false
            }],
            "vue/order-in-components": 0,
            "vue/attributes-order": 0,
            "vue/html-self-closing": 0
        }
    }
    ```
    关于eslint-plugin-vue的规则介绍，你可以看[这里](https://github.com/vuejs/eslint-plugin-vue#priority-b-strongly-recommended-improving-readability)

3. 安装vscode插件

    打开vscode,在扩展里搜索安装`eslint`和`Vetur`

    安装完成之后，打开vscode的设置，找到`eslint.validate`选项，在里面添加`"vue"`,然后保存。


现在，你就可以在vscode里对Vue代码使用eslint了，如果默认的规则你不满意的话，可以在eslint报error的时候查看相应的规则名，在`.eslint.json`里的`rule`选项里重新配置，就可以覆盖原来的规则了。

end
