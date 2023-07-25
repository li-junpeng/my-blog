## 解决: vue3 报错：`defineModel is not defined`

package.json 部分代码如下：
```json
{
  "dependencies": {
    "vue": "^3.3.4"  
  },
  "devDependencies": {
    "@vitejs/plugin-vue": "^4.2.3",
    "vite": "^4.3.9"
  }
}
```

`defineModel`宏默认是关闭的, 在使用的时候需要手动开启。vite.config.ts配置项如下:
```javascript
export default defineConfig({
    plugins: [
        vue({
            script: {
                // 开启defineModel
                defineModel: true
            }
        })
    ]    
})
```

开启后需要重启vue项目
