// import static org.junit.jupiter.api.Assertions.assertEquals;

// import org.junit.jupiter.api.Test;

public class Main {
  public static void main(String[] args) {
    System.out.println("Hello world!");
  }

  // @Test
  // void addition() {
  //     assertEquals(2, 1 + 1);
  // }
}npm install electron --save-dev
  {
    "name": "simple-web-browser",
    "version": "1.0.0",
    "main": "main.js",
    "scripts": {
      "start": "electron ."
    },
    "devDependencies": {
      "electron": "^25.0.0"
    }
  }const { app, BrowserWindow } = require('electron');
const path = require('path');

function createWindow () {
  const win = new BrowserWindow({
    width: 800,
    height: 600,
    webPreferences: {
      preload: path.join(__dirname, 'preload.js'),
      nodeIntegration: true
    }
  });

  // Load a default webpage (e.g., Google)
  win.loadURL('https://www.google.com');

  // Open DevTools (optional)
  win.webContents.openDevTools();
}

// When Electron is ready, create the browser window
app.whenReady().then(() => {
  createWindow();

  app.on('activate', function () {
    if (BrowserWindow.getAllWindows().length === 0) createWindow();
  });
});

// Quit the app when all windows are closed
app.on('window-all-closed', () => {
  if (process.platform !== 'darwin') app.quit();
});window.addEventListener('DOMContentLoaded', () => {
  console.log('Web page is loaded');
});npm start
