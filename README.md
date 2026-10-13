# TindaHUB — SIA V6

**Full title:** TindaHUB: An Integrated Mobile-Web Marketplace and Seller Operations System  
**Tagline:** One Hub. Every Transaction Connected.  
**Course:** Systems Integration and Architecture (MWA)

TindaHUB is a local marketplace prototype connecting buyer ordering, seller product and inventory operations, simulated payment processing, rider delivery, notifications, reports, audit logs, and integration logs through an Express REST API and SQLite database.

This README explains what to install, how to open the project in Visual Studio Code, and how to run it in a browser at `http://localhost:3000`.

## 1. What you need to install

Install these before running the project:

1. **Node.js 22 LTS (64-bit Windows installer).** Use Node.js 22 because this project's `package.json` requires Node `>=20 <23`. The tested setup guidance for this project is Node.js `v22.23.3`.
   - Official downloads: <https://nodejs.org/en/download>
   - Node.js 22 releases: <https://nodejs.org/dist/latest-v22.x/>
   - If you need the `v22.23.3` Windows x64 installer, open <https://nodejs.org/dist/v22.23.3/> and download `node-v22.23.3-x64.msi`.
   - npm is included with Node.js; you do not need to install npm separately.
2. **Visual Studio Code.** Download from <https://code.visualstudio.com/>.
3. **Internet access during setup.** `npm install` downloads the project's dependencies. After dependencies are installed, the app runs locally.

> **Important:** Node.js 24 does not match this project's declared engine range. Use Node.js 22 LTS. If the installer says a newer version is already installed, uninstall the existing Node.js version from Windows **Settings → Apps → Installed apps**, then install Node.js 22.

## 2. Extract the ZIP file

1. Download `SIA V6.zip`.
2. Open your Windows **Downloads** folder.
3. Right-click the ZIP file and choose **Extract All...**.
4. Extract it to a normal folder you can edit, such as `C:\Users\YOUR_USERNAME\Downloads\SIA V6`.
5. Open the extracted folder and find the project folder containing `package.json`, `server.js`, `index.html`, `script.js`, and `style.css`.

The ZIP already contains a top-level folder named `SIA V6`. If you first create a folder named `SIA V6` and then extract the ZIP into it, you may end up with a nested path such as:

`C:\Users\YOUR_USERNAME\Downloads\SIA V6\SIA V6`

That is okay. **The correct folder to open is the folder that directly contains `package.json` and `server.js`.** Do not open only the outer folder if the files are inside a second folder.

## 3. Open the correct folder in VS Code

1. Open **Visual Studio Code**.
2. Click **File → Open Folder...**.
3. Browse to the extracted project folder that contains `package.json` and `server.js`.
4. Select that folder and click **Select Folder**.
5. In the Explorer panel on the left, confirm that you can see files such as:
   - `package.json`
   - `server.js`
   - `index.html`
   - `script.js`
   - `style.css`
   - `schema.sql`
   - the `scripts`, `tests`, and `docs` folders

If those files are not visible, you may have opened the outer folder. Choose **File → Open Folder...** again and select the inner folder containing `package.json`.

## 4. Open Command Prompt in the VS Code terminal

The commands below work best in **Command Prompt (`cmd`)**. PowerShell may show an error that `npm.ps1` cannot be loaded because script execution is disabled. You do not need to change Windows security settings to avoid that error.

1. In VS Code, click **Terminal → New Terminal**.
2. If the terminal prompt starts with `PS`, it is PowerShell.
3. To switch the terminal profile:
   - Press `Ctrl + Shift + P`.
   - Type `Terminal: Select Default Profile`.
   - Choose **Command Prompt**.
   - Click **Terminal → New Terminal** again.
4. The prompt should look similar to `C:\Users\YOUR_USERNAME\Downloads\SIA V6\SIA V6>` and should **not** begin with `PS`.

If Command Prompt is already open in the correct project folder, continue to the next section.

## 5. Verify Node.js and npm

In the VS Code **Command Prompt** terminal, run each command separately:

```cmd
node -v
npm -v
```

The Node.js version should begin with `v22.` (for example, `v22.23.3`). npm should print a version number. If `node` is not recognized, finish installing Node.js and fully close and reopen VS Code.

If the terminal is not in the project folder, change directory. For example, if you extracted to the nested Downloads path above, run:

```cmd
cd "C:\Users\YOUR_USERNAME\Downloads\SIA V6\SIA V6"
```

Replace `YOUR_USERNAME` with your Windows account folder name. The easier option is to open the correct project folder in VS Code first; new terminals normally start there.

## 6. Install the project dependencies

Make sure the terminal is in the folder that contains `package.json`. Run:

```cmd
npm install
```

Wait for it to finish. This creates `node_modules` and may create `package-lock.json`. Warnings about deprecated packages do not always mean installation failed; look for a final error. If npm reports an error, do not continue until it is resolved.

If you see a PowerShell error mentioning `npm.ps1` or “running scripts is disabled,” switch to Command Prompt using Section 4 and retry `npm install` there.

If `better-sqlite3` fails to install, confirm you are using Node.js 22 LTS and have internet access to npm. See its troubleshooting guide: <https://github.com/WiseLibs/better-sqlite3/blob/master/docs/troubleshooting.md>.

## 7. Set up the database

The database is stored at `data/tindahub.sqlite` when the app runs.

### First-time setup (new database)

If this is a new installation and you do **not** need to keep an existing TindaHUB database, run:

```cmd
npm run init-db
```

The command creates the `data` folder if needed and initializes the database schema. The server inserts fictional demo accounts and sample products on first startup when they are absent.

### If you need to keep records from an earlier version

1. Stop the old TindaHUB server with `Ctrl + C` in its terminal.
2. Make a backup copy of the old `data` folder.
3. Copy the old `data` folder into the SIA V6 project folder (the same folder that contains `package.json`).
4. Do **not** delete the copied database or run reset/delete commands. If the old database has a different schema, back it up and verify compatibility before using it with the new version.

The ZIP does not include a database containing your personal or previously created records.

## 8. Start TindaHUB

In the same Command Prompt terminal, run:

```cmd
npm start
```

When the server starts, the terminal should show a message similar to:

```text
TindaHUB SIA V6 running at http://localhost:3000
```

Keep the terminal open while using the website. Closing the terminal or pressing `Ctrl + C` stops the local server.

## 9. Open the website in Chrome

1. Open Google Chrome (or another browser).
2. Enter this address in the address bar:

   <http://localhost:3000>

3. Press Enter.
4. The TindaHUB sign-in page should appear.

If the page does not open, check that the terminal still shows the server is running. If port 3000 is already in use, stop the other server or set a different `PORT` in a `.env` file and use that port in the browser.

## 10. Demo login accounts

Use these fictional classroom accounts:

| Role | Username | Password |
|---|---|---|
| Administrator | `admin` | `Admin123!` |
| Seller | `seller` | `Seller123!` |
| Buyer | `buyer` | `Buyer123!` |
| Rider | `rider` | `Rider123!` |

These are demo credentials only. Do not use them for a public deployment.

## 11. Recommended end-to-end demonstration

1. Sign in as **buyer**. Open Marketplace, add an in-stock product to the cart, enter a delivery address, and place an order.
2. Use the simulated payment action if available and confirm the payment/order status.
3. Sign in as **seller**. Manage the seller's products and inventory, review orders, pack an eligible paid order, and assign a rider.
4. Sign in as **rider**. Open assigned deliveries, start delivery, and mark the delivery as delivered.
5. Sign in as **admin**. Review dashboard summaries, user/role management, reports, audit logs, and integration logs.
6. Check that inventory movement references increase, and that audit log descriptions are readable.

These are recommended test steps; features should be verified in the running application before claiming that all tests passed.

## 12. Optional: run automated tests

With the server stopped or in a separate terminal opened to the project folder, run:

```cmd
npm test
```

Record the actual test result for project evidence. Do not state that tests passed unless the command completes successfully.

## 13. Troubleshooting

- **`npm` is not recognized:** Install Node.js 22 LTS, then close and reopen VS Code.
- **`npm.ps1 cannot be loaded` / scripts are disabled:** Switch to the Command Prompt terminal; do not change PowerShell execution policy just for this project.
- **`package.json` cannot be found:** The terminal is in the wrong folder. Use `dir` and make sure `package.json` is listed, or reopen the folder containing it in VS Code.
- **`better-sqlite3` installation fails:** Verify Node.js is v22 LTS and check internet access. Follow the official troubleshooting guide linked above.
- **Port 3000 is busy:** Stop the other local server, or set `PORT=3001` in `.env`, restart the server, and open `http://localhost:3001`.
- **Browser cannot connect:** Ensure `npm start` is still running and use the exact localhost URL printed in the terminal.
- **Login fails:** Use the exact demo credentials. If you copied an older database, the existing accounts may have been changed.
- **API returns 401:** Sign in again. **403** means the current role is not permitted to perform that action.

## 14. Project structure

```text
SIA V6/
├── index.html
├── style.css
├── script.js
├── server.js
├── schema.sql
├── package.json
├── .env.example
├── .gitignore
├── scripts/                  # database initialization, seeding, backup, restore
├── tests/                    # automated smoke tests
├── docs/
│   ├── PROJECT_DOCUMENTATION.md
│   ├── IMPLEMENTATION_STATUS.md
│   ├── API_AND_INTEGRATION.md
│   ├── REQUIREMENTS_TRACEABILITY.md
│   ├── TEST_PLAN_AND_RESULTS.md
│   ├── RISK_REGISTER.md
│   ├── TindaHUB.postman_collection.json
│   └── diagrams/             # Mermaid diagram source files
├── backups/                  # generated backups; not shipped with user data
└── data/                     # created at runtime; database is not included in ZIP
```

## 15. Technology and project limitations

- Frontend: HTML, CSS, vanilla JavaScript, and Fetch API.
- Backend: Node.js and Express REST API.
- Database: SQLite through `better-sqlite3`.
- Payment is simulated; no real payment gateway or money transfer is connected.
- Notifications are in-app; external SMS/email services are not connected.
- The application is designed for local classroom demonstration, not production deployment.
- Before any public deployment, review session storage, HTTPS, CSRF protection, secret management, account lifecycle, and monitoring.

## 16. Inventory references and audit logs

Inventory movements use readable references such as `INV-000001`, `INV-000002`, and so on, based on database-generated movement IDs. Audit logs use readable references such as `AUD-000123` and display plain-language summaries instead of raw JSON details. Verify these behaviors in the running app as part of the project demonstration.

## 17. Seller and administrator permissions

- Sellers create/edit their own products and manage inventory for their own products.
- Inventory restocking and inventory movement history are seller-scoped.
- Administrators do not see Products or Inventory in their navigation; server-side role checks restrict product and restock operations.
- Audit Logs and Integration Logs are administrator functions.

---

**Project version:** SIA V6 / TindaHUB 6.0.0  
**Local URL:** <http://localhost:3000>
