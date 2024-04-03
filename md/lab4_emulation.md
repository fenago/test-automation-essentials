### Lab: Emulation

You can use the test generator to generate tests using emulation so as to generate a test for a specific viewport, device, color scheme, as well as emulate the geolocation, language or timezone. The test generator can also generate a test while preserving authenticated state.

#### Emulate viewport size

Playwright opens a browser window with its viewport set to a specific width and height and is not responsive as tests need to be run under the same conditions. Use the --viewport option to generate tests with a different viewport size.

`playwright codegen --viewport-size=800,600 playwright.dev`

![](./images/220403118-7704b708-dea3-44b3-97a4-04c2b9d1d0fa.png)


#### Emulate devices

Record scripts and tests while emulating a mobile device using the --device option which sets the viewport size and user agent among others.

`playwright codegen --device="iPhone 13" playwright.dev`

![](./images/220922790-5c5a4d1a-e27d-4c9b-90ac-13cf9c925706.png)


#### Emulate color scheme

Record scripts and tests while emulating the color scheme with the `--color-scheme` option.

`playwright codegen --color-scheme=dark playwright.dev`

![](./images/220930714-737647fd-ae99-4dd3-b7a4-4f3eb4fe712d.png)

#### Emulate geolocation, language and timezone

Record scripts and tests while emulating timezone, language & location using the --timezone, --geolocation and --lang options. Once the page opens:

1. Accept the cookies
2. On the top right click on the locate me button to see geolocation in action.

`playwright codegen --timezone="Europe/Rome" --geolocation="41.890221,12.492348" --lang="it-IT" bing.com/maps`

![](./images/220932413-f2943956-dd38-4560-94b9-51968076210d.png)


#### Preserve authenticated state

Run codegen with `--save-storage` to save cookies and localStorage at the end of the session. This is useful to separately record an authentication step and reuse it later when recording more tests.

`playwright codegen github.com/microsoft/playwright --save-storage=auth.json`

![](./images/220929429-8756ec49-fbf2-46e0-8f41-d25f5f5a6623.png)


#### Login

After performing authentication and closing the browser, auth.json will contain the storage state which you can then reuse in your tests.

![](./images/220561688-04b2b984-4ba6-4446-8b0a-8058876e2a02.png)

Make sure you only use the auth.json locally as it contains sensitive information. Add it to your .gitignore or delete it once you have finished generating your tests.

**Load authenticated state**

Run with `--load-storage` to consume the previously loaded storage from the auth.json. This way, all cookies and localStorage will be restored, bringing most web apps to the authenticated state without the need to login again. This means you can can continue generating tests from the logged in state.

`playwright codegen --load-storage=auth.json github.com/microsoft/playwright`

![](./images/220928211-ca1d4dc9-9966-414e-ab23-a3ef1d2d5ed9.png)

