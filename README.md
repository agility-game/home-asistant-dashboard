[![Build and Publish storybook to GitHub Pages](https://github.com/agility-game/home-assistant-dashboard/actions/workflows/deploy.yaml/badge.svg)](https://github.com/agility-game/home-assistant-dashboard/actions/workflows/deploy.yaml)

home-assistant-dashboard
# Home Assistant Dashboard

Based on "Home Assistant Dashboard" at https://github.com/shannonhochkins/ha-dashboard 

**NOTE**: The above repository has moved and can now be found as "ha-component-kit" at https://github.com/shannonhochkins/ha-component-kit and accompanying documentation at https://shannonhochkins.github.io/ha-component-kit/?path=/story/introduction-overview--default

Based on "Storybook for React tutorial" at https://storybook.js.org/tutorials/intro-to-storybook/react/en/get-started/

Based on "Problems and Solutions Upgrading to Storybook 7" at https://betterprogramming.pub/problems-and-solutions-upgrading-to-storybook-7-62c868b23af4

The documentation can be read at https://agility-game.github.io/home-assistant-dashboard/

Publish Storybook (inside ```docs``` directory) to Chromatic's secure CDN for the first time with the following command:

```
npx chromatic --project-token=chpt_98d934ebe677155
```

After a successful publication, our ```docs``` can now be seen at https://www.chromatic.com/setup?appId=6544ebbfe3db6d453bcf3c65

We can now run the publish script from within the ```docs``` directory or in CI with ```npm run chromatic``` or ```yarn chromatic```.

ℹ Your project token was added to the script via the --project-token flag.
If you're running Chromatic via continuous integration, we recommend setting
the CHROMATIC_PROJECT_TOKEN environment variable in your CI environment.
You can then remove the --project-token from your package.json script.

*****WE ARE HERE (inside docs folder)*****: https://storybook.js.org/tutorials/intro-to-storybook/react/en/deploy/

**WARNING**: In our ```docs``` directory, where we are using StoryBook, one needs to upgrade yarn to at least version 3 to avoid build errors. 

```yarn upgrade```

## 100 - Introduction

See [README.md](./100/README.md)

## 200 - Requirements

See [README.md](./200/README.md)

## 300 - Building Our Application

See [README.md](./300/README.md)

## 400 - Conclusion

See [README.md](./400/README.md)
