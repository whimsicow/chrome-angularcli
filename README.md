# Angular Unit and e2e Tests in a Docker container
This Docker image allows you to run Angular e2e and unit tests in a headless machine like a CI server. It installs the latest version of Chrome and AngularCLI. Please ensure your ChromeDriver supports the version of Chrome you are using.

Link to Docker Hub: https://hub.docker.com/r/sabbey37/chrome-angularcli/

ChromeDriver + Chrome compatibility: http://chromedriver.chromium.org/downloads

### Karma config:
```javascript
hostname: '127.0.0.1',
browsers: ['Chrome_no_sandbox'],
customLaunchers: {
  Chrome_no_sandbox: {
    base: 'Chrome',
    flags: ['--no-sandbox', '--headless', '--disable-gpu', '--remote-debugging-port=9222']
  }
},
```
### To run unit tests:
```bash
ng test --browsers Chrome_no_sandbox --watch=false
```

### Protractor config:
```javascript
baseUrl: 'http://127.0.0.1:4200',
capabilities: {
    'browserName': 'chrome',
    'chromeOptions': {
      'args': ['--no-sandbox', '--headless', '--disable-gpu', '--disable-browser-side-navigation']
    }
},
```

### To run e2e tests:
```bash
ng e2e --host 127.0.0.1
```
