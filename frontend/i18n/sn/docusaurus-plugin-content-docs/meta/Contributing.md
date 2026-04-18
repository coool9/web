---
title: Contributing
sidebar_label: Contributing
description: open.mp ain sa-mp je documentation main kien madad kaje.
---

Hi documentation main ker b madad kre saghe tho. Tawhan khe bs hik [GitHub](https://github.com) account ain kujh time tho khape. Tawhan khe Git janran ji b zaroorat kanhe. Tawhan sbh kujh web tan kare sagho tha!

Jekadhen tawhan kehn hikri boli khe maintain karanr tha chahyo tha t PR karyo [`CODEOWNERS`](https://github.com/openmultiplayer/web/blob/master/CODEOWNERS) file te ain hik line thhahyo pehnji boli ji directory ain username san gad.

## Editing Content

Hr page je  hethhan hik buttonr ahe jeko tawhan khe unhe page je GitHub dahn wathhi weendo.

![Edit this page link present on each wiki page](https://assets.open.mp/assets/images/contributing/edit-this-page.png)

Misaal tor [SetVehicleAngularVelocity](../scripting/functions/SetVehicleAngularVelocity) khe click karanr san tawhan [hin page](https://github.com/openmultiplayer/web/edit/master/frontend/docs/scripting/functions/SetVehicleAngularVelocity.md) dahn weenda jithe tawhan wt hik text editor hoondo pehnji changes karanr laye (je tawhan GitHub mn log in thiyal ahyo).

Pehnjun tabdeelyun kare hik "Pull Request" thhahyo. Inhe jo matlab ahe t wiki maintainer ain bya community ja member tawhan ji tabdeelin jo jayizo wathhanda, faislo kanda t chha inhe khe wadheek tabdeelin ji zaroorat ahe ya na ain poe merge kanda.

## Adding New Content

Naun mawaad add karanr thoro wadheek pecheeda ahe. Tawhan bin tareekn san kare sagho tha:

### GitHub Interface

When browsing a directory on GitHub, there's an Add file button on the top right corner of the file list:

![Add file button](https://assets.open.mp/assets/images/contributing/add-new-file.png)

You can either upload a Markdown file you've written already or write it directly into the GitHub text editor.

File wt _zaroor_ `.md` extension ain Markdown huje. Markdown laye wadheek maloomat laye diso [hi guide](https://guides.github.com/features/mastering-markdown/).

Jadhen uho thi wanje, dabayo "Propose new file" ain a Pull Request khuli weendi review laye.

### Git

Je tawhan khe Git istemaal karnri ahe t sirf clone karyo hin Wiki repository khe:

```sh
git clone https://github.com/openmultiplayer/web.git
```

Open it in your favourite editor. I recommend Visual Studio Code as it has some great tooling for editing and formatting Markdown files. As you can see, I'm writing this using Visual Studio Code!

![Visual Studio Code markdown preview](https://assets.open.mp/assets/images/contributing/vscode.png)

Aun ba extension recommend tho karyan pehnjo experience solo karanr laye:

- [markdownlint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint) by David Anson - this is an extension that makes sure your Markdown is formatted correctly. It prevents some syntactical and semantic mistakes. Not all the warnings are important, but some can help improve readability. Use best judgement and if in doubt, just ask a reviewer!
- [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) by the Prettier.js Team - this is a formatter that will automatically format your Markdown files so they all use a consistent style. The Wiki repository has some settings in its `package.json` that the extension should automatically use. Be sure to enable "Format On Save" in your editor settings so your Markdown files will be automatically formatted every time you save!

## Notes, Tips and Conventions

### Internal Links

Don't use absolute URLs for inter-site links. Use relative paths.

- ❌

  ```md
  To be used with [OnPlayerClickPlayer](https://www.open.mp/docs/scripting/callbacks/OnPlayerClickPlayer)
  ```

- ✔

  ```md
  To be used with [OnPlayerClickPlayer](../callbacks/OnPlayerClickPlayer)
  ```

`../` means "go up one directory" so if the file you're editing is inside the `functions` directory and you're linking to `callbacks` you use `../` to go up to `scripting/` then `callbacks/` to enter the callbacks directory, then the filename (without `.md`) of the callback you want to link.

### Images

Images go inside a subdirectory inside `/static/images`. Then when you link an image in a `![]()` you just use `/images/` as the base path (no need for `static` that's just for the repository).

If in doubt, read another page that uses images and copy how its done there.

### Metadata

The first thing in _any_ document here should be metadata:

```mdx
---
title: My Documentation
sidebar_label: My Documentation
description: This is a page about stuff and things and burgers, yay!
---
```

Every page should include a title and a description.

For a full list of what can go between the `---`, check out [the Docusaurus documentation](https://docusaurus.io/docs/markdown-features#markdown-headers).

### Headings

Don't create a level 1 heading (`<h1>`) with `#` as this is generated automatically. Your first heading should _always_ be `##`

- ❌

  ```md
  # My Title

  This is documentation for ...

  # Sub-Section
  ```

- ✔

  ```md
  This is documentation for ...

  ## Sub-Section
  ```

### Use `Code` Snippets For Technical References

When writing a paragraph that contains function names, numbers, expressions or anything that's not standard written language, surround them with \`backticks\` like that. This makes it easier to separate language for describing things from references to technical elements such as function names and pieces of code.

- ❌

  > The fopen function will return a value with a tag of type File:, there is no problem on that line as the return value is being stored to a variable also with a tag of File: (note the cases are the same too). However on the next line the value 4 is added to the file handle. 4 has no tag [...]

- ✔

  > The `fopen` function will return a value with a tag of type `File:`, there is no problem on that line as the return value is being stored to a variable also with a tag of `File:` (note the cases are the same too). However on the next line the value `4` is added to the file handle. `4` has no tag

In the above example, `fopen` is a function name, not an English word, so surrounding it with `code` snippet markers helps distinguish it from other content.

Also, if the paragraph is referring to a block of example code, this helps the reader associate the words with the example.

### Tables

If a table has headings, they go in the top part:

- ❌

  ```md
  |         |                                      |
  | ------- | ------------------------------------ |
  | Health  | Engine Status                        |
  | 650     | Undamaged                            |
  | 650-550 | White Smoke                          |
  | 550-390 | Grey Smoke                           |
  | 390-250 | Black Smoke                          |
  | < 250   | On fire (will explode seconds later) |
  ```

- ✔

  ```md
  | Health  | Engine Status                        |
  | ------- | ------------------------------------ |
  | 650     | Undamaged                            |
  | 650-550 | White Smoke                          |
  | 550-390 | Grey Smoke                           |
  | 390-250 | Black Smoke                          |
  | < 250   | On fire (will explode seconds later) |
  ```

### Cleaning Up

The conversion likely won't be perfect. So you'll have to do a bit of manual cleanup. The formatting extensions listed above should help with that but you may still need to just spend some time doing manual work.

If you don't have time, don't worry! Submit an unfinished draft and someone else can pick up where you left off!

## License Agreement

Sabhni open.mp projects wt ahe [Contributor License Agreement](https://cla-assistant.io/openmultiplayer/homepage). Hin jo bunyaadi maqsad iho ahe t tawhan asan khe ijazat dyo tha pehnje kam khe istemaal karanr ji, ain hik open-source license men aanrnr. Jadhen tawhan pehren chakar hik Pull Request kholeenda, t CLA-Assistant bot hik link post kando jehn san tawhan uho agreement sign kare sagho tha.
