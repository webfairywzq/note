17——vue 项目完成后的操作

1. 给 axios 设置 defaults.baseURL：

   ```javascript
   axios.defaults.baseURL = 'url地址'
   ```

   但是正常项目有 开发环境 和 生产环境 之分，所以

2. 设置 baseURL 时根据对应的 process.env.NODE_ENV 进行动态设置：

   ```javascript
   // process.env.NODE_ENV 有两个值：development 和 production
       ★. npm run serve ------process.env.NODE_ENV 是 ：development
       ★. npm run build ------process.env.NODE_ENV 是 ：production
   // 应这样设置：
       const baseURL = process.env.NODE_ENV === 'development' ? '开发环境url' : '生产环境url'
       axios.defaults.baseURL = baseURL;
   
   ```

3. npm run build（打包） 后默认产生的静态资源：

   1. 默认：

      直接存放到服务器根目录下

   2. 如果说项目需要在服务器的某个文件夹下：

      ```javascript
      // 需在 vue.config.js 中配置：
      module.exports = {
          baseUrl:'/文件夹名称/' 
          // 注意 baseUrl 单词别写错
      }
      
      // 当打包放在指定文件夹下后，再运行 npm run serve 此时项目访问地址变成 localhost:8080/文件夹名称/,如果不想这样显示（想要显示 localhost:8080/），需配置：
      module.exports = {
          baseUrl:process.env.NODE_ENV === 'development' ? '/' : '/文件夹名称/'
      }
      ```

   3. 如果要求能够直接打开：

      ```javascript
      // 需在 vue.config.js 中配置：
      module.exports = {
          baseUrl:'./'
      }
      ```
