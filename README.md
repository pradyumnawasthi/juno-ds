#  Building the Design Tokens Pipeline for Juno

Defining design tokens on Token Studio. Pushing to GitHub. Using token-transformer which transforms tokens from Tokens Studio to something Style Dictionary can read, removing any math operations or aliases, only resulting in raw values.

The GitHub action will automatically generate tokens to the tokens/ directory that can then be read by Style Dictionary, which will output tokens to the format you defined in build.js - css variables will be generated in the output directory.

## Style Dictionary

Amazon created Style Dictionary and their page has a pretty good description of the tool.

> Style Dictionary is a build system that allows you to define styles once, in a way for any platform or language to consume. A single place to create and edit your styles, and a single command exports these rules to all the places you need them - iOS, Android, CSS, JS, HTML, sketch files, style documentation, or anything you can think of. It is available as a CLI through npm, but can also be used like any normal node module if you want to extend its functionality.

For example, you may have a color tokens file:

```
{
  "color": {
    "base": {
      "gray": {
        "light": {
          "value": "#CCCCCC"
        },
        "medium": {
          "value": "#999999"
        },
        "dark": {
          "value": "#111111"
        }
      },
      "red": {
        "value": "#FF0000"
      },
      "green": {
        "value": "#00FF00"
      }
    }
  }
}
```

That’s great, but in order to consume those tokens in UI components, you want to export that to iOS .swift file, or an Android .xml file, or as CSS custom properties or JS variables for the web. Style Dictionary allows you to do this easily with a great API to create your own export formats (through transforms/transformGroups).
