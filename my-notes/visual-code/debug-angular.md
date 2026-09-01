# Angular Remote Debugging Setup

You will see the debug in your VS and Chrome developer mode 

1. **Add remote debugging to your app and enable source maps**

Add this to `angular.json`:

```json
"build": {
  "options": {
    "sourceMap": true
  }
}
```

2. **Start your application**

3. **Create a launch file**

```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Launch Chrome",
      "request": "launch",
      "type": "chrome",
      "url": "http://localhost:3000", // <-- your port
      "webRoot": "${workspaceFolder}"
    }
  ]
}
```

4. **Go to the Debug view and launch Chrome**

5. **Open Developer Tools (F12)** in the browser and verify that your `.ts` files appear under:

```text
webpack://
```

or

```text
src/
```

# Node JS only Remote Debugging Setup

1. **Add remote debugging to your node app and enable source maps**
   You need to enable source maps !! 

Add this to `angular.json`:

```json
"build": {
  "options": {
    "sourceMap": true
  }
}
```
or open package.json and add "--enable-source-maps" 
```
"scripts": {
    "start": "node server.js",
    "start:angular-dev": "ng serve --proxy-config proxy.conf.json",
    "start:express-dev": "cross-env NODE_ENV=development nodemon --enable-source-maps --inspect start.js", <---- here 
  
```
2.  **Go to the Debug view and launch Node**
3.  **It will read you package.json and select the start that you want to use for instance, start:angular-dev**

More info look this video 
https://www.youtube.com/watch?v=XHEnQM_NieU
