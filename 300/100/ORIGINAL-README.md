# 100 - Project Setup

## 100 - Getting Started

Based on "Getting Started" at https://github.com/shannonhochkins/ha-dashboard

Install the software from this repository on a system that has NodeJS installed, for generating the build files necessary for copying into Home Assistant later. Alternatively, open this repository in a cloud-based workspace such as offered by GitPod.

```
npm install
```

Build the dist folder and its content

```
npm run build
```

Run a development server

```
npm run start
```

Add the following to your ```configuration.yaml``` file in Home Assistant:

```
panel_custom:
  - name: react-panel-dev
    sidebar_title: React Panel
    sidebar_icon: mdi:react
    url_path: react-panel-dev
    js_url: http://0.0.0.0:8080/main.js
    embed_iframe: true
    config:
      name: World
```

Restart Home Assistant.

## 200 - Deploy

Let's assume you've created a directory under the www folder called ```react-panel```. Also add this to the package.json ```panelServingUrl```

To deploy it, run ```npm run build``` on the system that is intended for the generation of the build files (only).

This will generate a new build of the panel in the ```dist``` folder on that system. Copy the contents of this folder and place it in ```<home assistant config>/www/react-panel```.

This will make it available from Home Assistant via the url ```/local/react-panel/main.js```.

I create a second custom panel, notice the missing "-dev" which will be the production dashboard.

```
panel_custom:
  - name: react-panel
    sidebar_title: React Panel
    sidebar_icon: mdi:react
    url_path: react-panel-prod
    js_url: /local/react-panel/main.js
    embed_iframe: true
    config:
      name: World
```

## 300 - Custom Redirect (Optional)

Custom Redirect from the default dashboard so devices auto redirect to the react-panel

This will simply find the react-panel element in the sidebar and click it if it's not active, add this javascript file to the default dashboard resources.

```
export default function customRedirect( {
    const homeAssistant = document.querySelector('home-assistant');
	const root = homeAssistant.shadowRoot.querySelector('home-assistant-main').shadowRoot;
	const sidebarRoot = root.querySelector('ha-sidebar').shadowRoot;
	const reactPanelElement = sidebarRoot.querySelector('paper-listbox').querySelector('a[data-panel="react-panel"]:not([class*="selected"])');
	if(!reactPanelElement) { return; }
	reactPanelElement.click();
}

customRedirect();
```
