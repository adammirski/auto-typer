# Auto-Typer for Guacamole labs

Copy and paste often does not work in lab VMs opened through Guacamole (in the browser). This tool **types** your text into the VM, key by key, so you don't need the clipboard.

There are two tools inside `auto-typer.zip`:

- **Guac Typer**: a browser bookmark. Nothing to install. Works on Mac, Windows, Linux and in any browser. **Try this first.**
- **Desktop auto-typer**: a small Mac/Windows app. Use it if the bookmark does not work for you.

## 1. Download

1. Click this link: **[Download auto-typer.zip](https://github.com/adammirski/auto-typer/raw/main/auto-typer.zip)**
   (or click `auto-typer.zip` in the file list above, then the **Download raw file** button).
2. Unzip it:
   - **Mac:** open **Downloads** and double-click `auto-typer.zip`. You now have a folder called `auto-typer`.
   - **Windows:** open **Downloads**, right-click `auto-typer.zip`, choose **Extract All...**, then **Extract**.

## 2. Option A: the bookmark (no install)

1. Open `auto-typer/install.html` in your browser (double-click it).
2. Follow **Step 1** on that page: drag the blue **Guac Typer** button to your bookmarks bar.
3. Open your VM in Guacamole, click the **Guac Typer** bookmark, paste your text into the panel, click inside the VM, then click **Type it**.

## 3. Option B: the desktop app on a Mac

### Step 1. Install Python (once)

The Python that comes with macOS is too old for this app (you could not type in its window). Install the current one:

1. Go to https://www.python.org/downloads/ and click the yellow **Download Python** button.
2. Open the downloaded `.pkg` file and click through the installer.

Check it worked. Open **Terminal** (Cmd+Space, type `Terminal`, press Enter) and run:

```
python3 -c "import tkinter; print(tkinter.TkVersion)"
```

You should see **8.6** or higher. If you see **8.5**, close Terminal (Cmd+Q), open it again and retry.

> Homebrew users can instead run `brew install python python-tk`.

### Step 2. Start the app

In Terminal, run these one at a time:

```
cd ~/Downloads/auto-typer/desktop
```

```
bash run-mac.command
```

The first start takes about a minute (it downloads one small library). Later starts are instant.

### Step 3. Allow keystrokes (once)

macOS blocks apps from typing until you allow them. If a **"Permission needed"** message appears:

1. Click **OK** and close the auto-typer window.
2. Open **System Settings > Privacy & Security > Accessibility**.
3. Turn **Terminal** on. If it is not in the list, click **+**, open **Applications > Utilities**, pick **Terminal**.
4. Quit Terminal completely with **Cmd+Q**, open it again, and repeat Step 2.

Without this permission, the app looks like it is typing but nothing arrives.

### Step 4. Use it

1. Paste your text into the box, or click **Paste clipboard**.
2. Click **Start**.
3. During the 5 second countdown, click inside the VM where the text should go.
4. Do not touch the keyboard until the status says **Done**.

**To stop early:** move the mouse into the **top-left corner** of the screen.

## 4. Option C: the desktop app on Windows

### Step 1. Find the app folder

Make sure you used **Extract All** in section 1. Double-clicking the zip only *shows* the files, and the app cannot run from there.

In the extracted folder, open `auto-typer`, then `desktop`.

### Step 2. Install Python (once)

1. Go to https://www.python.org/downloads/ and click the yellow **Download Python** button.
2. Run the installer. On the first screen, **tick "Add python.exe to PATH"** at the bottom, then click **Install Now**.

Check it worked. Press the **Windows key**, type `cmd`, press Enter, and run:

```
py -c "import tkinter; print(tkinter.TkVersion)"
```

You should see **8.6** or higher. If you see *"'py' is not recognized"*, close the window, open a new one and retry; if it still fails, run the installer again and choose **Modify**.

### Step 3. Start the app

Double-click **`run-windows.bat`** in the `desktop` folder.

- If a blue **"Windows protected your PC"** box appears, click **More info**, then **Run anyway**. Windows shows this for any script downloaded from the internet.
- The first start opens a black window for about a minute while it downloads one small library. Later starts are instant.

No extra permission is needed on Windows.

**Nothing opens?** In the `desktop` folder, click the address bar, type `cmd`, press Enter, and run:

```
.venv\Scripts\python autotyper.py
```

The error message it prints tells you what is wrong. Some antivirus programs block apps that type keys; if yours does, allow it or use the bookmark (Option A) instead.

### Step 4. Use it

1. Paste your text into the box, or click **Paste clipboard**.
2. Click **Start**.
3. During the 5 second countdown, click inside the VM where the text should go.
4. Do not touch the keyboard until the status says **Done**.

**To stop early:** press **Esc**, or move the mouse into the **top-left corner** of the screen.

## Tips

- **Each line break is pressed as Enter**, so every line runs as soon as it is typed. For long multi-line PowerShell, type it into Notepad, save it as a `.ps1` file and run that instead.
- **Letters go missing?** Raise **Char delay** to 30 or 50.
- **Fix smart quotes** (on by default) turns curly quotes `“ ” ‘ ’` and long dashes from web pages and PDFs into plain `" ' -`, which the terminal understands.
- **Enter at end** is off by default, so you can check the command before it runs.
- In **vim**, run `:set paste` before typing, so vim does not add extra indentation.

More details are in `README.md` inside the zip.
