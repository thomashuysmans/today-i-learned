## How to find which proces is running on which port on macOS	

Today, I was playing around with Dapr and I need to see which proces whas using the port I needed. In macOs, and Linux, you have the [lsof command](https://en.wikipedia.org/wiki/Lsof). 

If you want to know which proces is using which port, execute  following command in the terminal window:

```bash
lsof -i TCP:portnumber
```

