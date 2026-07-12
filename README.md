# Stratis V4 – Development Environment Setup

## Prerequisites

### 1. Install NVM (Node Version Manager)

Install **NVM for Windows** so you can easily switch between the required Node.js versions.

The project uses:

* **Integration Main:** Node.js **16.20.2**
* **Newsletter:** Node.js **12.22.12**

> **Note:** If a required Node.js version is not installed, you can install it using:
>
> ```bash
> nvm install <version>
> ```
>
> Example:
>
> ```bash
> nvm install 16.20.2
> nvm install 12.22.12
> ```

---

# Integration Main Setup

## 1. Clone the Repository

Clone the `integration-main` repository to your local machine.

Example location:

```text
C:\Users\<YourUser>\Desktop\chenocom\resopital.mc\integration-main
```

Replace `<YourUser>` with your Windows username.

---

## 2. Create the VS Code Settings File

Create the following file if it does not already exist:

```text
C:\Users\<YourUser>\Desktop\chenocom\resopital.mc\integration-main\.vscode\settings.json
```

Paste the following configuration into the file:

```json
{
    "stylelint.enable": true,
    "css.validate": false,
    "scss.validate": false,
    "stylelint.validate": [
        "css",
        "scss"
    ],
    "editor.codeActionsOnSave": {
        "source.fixAll.stylelint": "always"
    },
    "editor.defaultFormatter": "stylelint.vscode-stylelint",
    "[html]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    }
}
```

---

## 3. Switch to the Required Node Version

```bash
nvm use 16.20.2
```

---

## 4. Install Dependencies

```bash
npm install
```

---

## 5. Run the Project

```bash
gulp
```

This starts the Integration Main project.

---

# Newsletter Setup

## 1. Switch to the Required Node Version

```bash
nvm use 12.22.12
```

---

## 2. Install Dependencies

```bash
npm install
```

---

## 3. Start the Newsletter Project

```bash
npm run inline-watch
```

This starts the Newsletter project in watch mode.

---

# Troubleshooting

### Unable to Install Node.js 12.22.12 with NVM

If the following command does not work:

```bash
nvm install 12.22.12
```

You can manually install Node.js 12.22.12:

1. Download the **Windows ZIP** version of **Node.js 12.22.12** from the official Node.js website or another trusted source.
2. Extract the downloaded folder.
3. Copy the extracted folder into the NVM installation directory:

```text
C:\Users\<YourUser>\AppData\Local\nvm
```

For example, after copying, you should have a folder similar to:

```text
C:\Users\<YourUser>\AppData\Local\nvm\v12.22.12
```

Replace `<YourUser>` with your Windows username.

### Enable Hidden Folders

The **AppData** folder is hidden by default in Windows.

To make it visible:

1. Open **File Explorer**.
2. Click **View**.
3. Enable **Hidden items**.

You will then be able to navigate to:

```text
C:\Users\<YourUser>\AppData\Local\nvm
```

#----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Font setup guide

## How to change the main font

1. Open the main typography variables file:
   - [src/scss/utils/_config.scss](src/scss/utils/_config.scss)

2. Change the variable value for the main font:
   ```scss
   --typo-1: 'Raleway', Arial, Tahoma, sans-serif;
   ```
   Replace `Raleway` with the font you want to use, for example:
   ```scss
   --typo-1: 'Poppins', Arial, Tahoma, sans-serif;
   ```

3. Make sure the font files are available locally in:
   - [src/fonts](src/fonts)

4. Add matching `@font-face` rules in:
   - [src/scss/base/_typography.scss](src/scss/base/_typography.scss)

5. Rebuild the project so the new styles are generated.

## Notes

- The mixin used in components only sets `font-family`, `font-size`, `font-weight`, and `font-style`.
- It does not load fonts by itself.
- If the font name in the CSS does not match the `@font-face` declaration, the browser will fall back to another font.

## Example

If you want to use Poppins instead of Raleway:

```scss
/* in src/scss/utils/_config.scss */
--typo-1: 'Poppins', Arial, Tahoma, sans-serif;
```

And in [src/scss/base/_typography.scss](src/scss/base/_typography.scss), define the Poppins `@font-face` entries for the required weights.

##How to add a new SCSS file to the project

To make a new style file work, you need to add it to src/scss/core.scss.


Create your new partial file, e.g. src/scss/components/_exemple.scss
Import it in src/scss/core.scss:

scss@import 'components/exemple';
