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
