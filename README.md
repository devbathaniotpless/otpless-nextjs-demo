[![OTPless](https://d1j61bbz9a40n6.cloudfront.net/website/home/v4/logo/white_logo.svg)](https://otpless.com/platforms/react)

# Next Demo : Otpless Floater

## Steps to add OTPless SDK to your Next Website

1. **Add OTPLESS Script as utils function**

> Add the following code to your utils/initOtpless.ts in root directory.

```JavaScript
  export const initOTPless = (callback: Function) => {
  const otplessInit = Reflect.get(window, "otplessInit");

  const loadScript = () => {
    const isScriptLoaded = document.getElementById("otplessIdScript");
    if(isScriptLoaded) return;

    const script = document.createElement("script");
    script.src = "https://otpless.com/auth.js";
    script.id = "otplessIdScript";
    script.setAttribute("cid","YOUR_CID");
    document.body.appendChild(script);
  };

  otplessInit ? otplessInit() : loadScript();

  Reflect.set(window, "otpless", callback);
};

```

2. **Load the script in Login/Signup component and add callback function**

> - Add following code in Login/Signup component.
> - retrive data using **otplessUser** object

```jsx
  useEffect(()=>initOTPless(callback),[]);

  const callback = (otplessUser:any) => {
    alert({otplessUser});
    // your code here
  };
```

### This demo implementation adds extra modularity, scalability and reusability to the otpless-auth sdk


### Integration Options

- [OTPless-Page](https://github.com/sjariN/otpless-next-demo/)
- [OTPless-Page-OnClick](https://github.com/sjariN/otpless-next-demo/tree/on-button-click-login-page)
- [OTPless-Floater](https://github.com/sjariN/otpless-next-demo/tree/widget)
- [OTPless-Floater-OnClick](https://github.com/sjariN/otpless-next-demo/tree/on-button-click-widget)

### Usage

> **Prequisite** [NodeJS](https://nodejs.org/en)

- Install Packages

    ```bash
    npm install
    ```

- Run the demo

    ```bash
    npm run dev
    ```

- Open [localhost:3000](http://localhost:3000) in your browser
- Switch branches to check out available options to integrate *OTPless* in your project.


> Received User Data Format  

```json
// otpless user Format
{
    "token": "xxxxxxxxxxxxxxxxxxxxxxxxxxxx",
    "timestamp": "YYYY-MM-DD HH:MM:SS",
    "timezone": "+XX:XX",
    "mobile": {
        "name": "User Name",
        "number": "User Mobile Number"
    },
    "email": {
        "name": "User Name ",
        "email": "User Email"
    }
}
```