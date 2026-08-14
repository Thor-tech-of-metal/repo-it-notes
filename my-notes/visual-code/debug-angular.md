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

More info look this video 
https://www.youtube.com/watch?v=XHEnQM_NieU
