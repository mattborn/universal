# universal

Render the same component in React Native, Sketch, and your browser.

## How this monorepo was assembled

Please note, all packages used in this repo are going to evolve and dependency hell will ensue.

When I asked my colleague [Chase](http://chasem.co) why an out-of-the-box, render-universal-components-everywhere monorepo doesn’t already exist, he replied with _“Because that would just be too good.”_ My short-term goal in creating this repo is to help folks new to Universal Rendering get started quickly. My long-term goal in documenting how I created this repo is to inspire others to accept the volatility and understand some gumption and up front effort is required to get each of these frameworks to play nicely together and develop for all of these environments at the same time.

All of this is [inspired by React Native](airbnb.io/react-sketchapp/docs/guides/universal-rendering.html), so we’ll start a new project in [Expo](https://expo.io). This gives us a working App.js entry file backed by the usual suspects in a React Native project—assets, dependencies, dotfiles, and the tiniest package.json. With a single click and QR code scan, you have primitives rendered (with slow hot-reloading) on your phone.

Now we’re gonna convert this to a monorepo to support rendering in Sketch—the inevitible convergence of code with design tools. We’ll copy dependencies, scripts, and `skpm` config from [react-sketchapp’s basic setup example](https://github.com/airbnb/react-sketchapp/blob/master/examples/basic-setup/package.json) and `npm install`. We’ll also copy over the `src` folder into the root folder of our Expo project and `npm run render`. [Thanks, Jon!](https://airbnb.design/painting-with-code)

Caveat #1: Due to [a tiny oversight at the time of this writing](https://github.com/airbnb/react-sketchapp/issues/225), I had to manually change `"react-sketchapp": "^0.12.1",` to `"react-sketchapp": "^1.0.0",` in `package.json`. Try this if rendering  in Sketch is not working for you, otherwise ignore this caveat.

Finally, let’s get this in a web browser. All I did was [follow Fredrik’s directions here](http://fredrik.anderzon.se/2016/12/04/adding-create-react-app-scripts-to-an-existing-project) to `npm i --save-dev react-scripts`, copy the `package.json` scripts over, and get a `public` folder with create-react-app’s default `index.html`. Run  and add [Thanks, Fredrick!](http://fredrik.anderzon.se/2016/12/04/adding-create-react-app-scripts-to-an-existing-project)

Caveat #2: Because I started with the Expo XDE react-native scaffolding, I had to manually change `"react` and `"react-test-renderer"` to `"^16.2.0"`. At the time of this writing, [Expo SDK is using a later version](https://github.com/expo/expo-sdk/blob/baed2a038c37a516dd2118b8e542fbc85b3674dd/package.json#L71) of `react` than [Expo XDE](https://github.com/expo/xde/blob/b01e119dd947f845c15b7252eebb23481ed39ee8/package.json#L117), so I expect this to catch up eventually. Try this if rendering in the browser is not working for you, otherwise ignore this caveat.
