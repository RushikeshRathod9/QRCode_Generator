# QR Code Generator

A simple QR Code Generator built using Python with a graphical user interface (GUI) created using Tkinter.

## Features
- Generate QR codes from text or URLs.
- Save the QR code as an image file.
- User-friendly interface with Tkinter.

## Requirements
Ensure you have Python installed on your system. Install the required dependencies using:
```bash
pip install qrcode[pil] tkinter
```

## Usage
1. Run the script:
   ```bash
   python qr_generator.py
   ```
2. Enter the text or URL you want to convert into a QR code.
3. Click the "Generate QR Code" button.
4. Preview the generated QR code.
5. Click "Save" to store the QR code as an image file.

## Example Code
```python
import qrcode
import tkinter as tk
from tkinter import filedialog, messagebox
from PIL import Image, ImageTk

def generate_qr():
    text = entry.get()
    if text:
        qr = qrcode.make(text)
        qr.save("temp_qr.png")
        img = Image.open("temp_qr.png")
        img = ImageTk.PhotoImage(img)
        qr_label.config(image=img)
        qr_label.image = img
    else:
        messagebox.showerror("Error", "Please enter text")

def save_qr():
    file_path = filedialog.asksaveasfilename(defaultextension=".png", filetypes=[("PNG files", "*.png")])
    if file_path:
        qr = qrcode.make(entry.get())
        qr.save(file_path)
        messagebox.showinfo("Saved", "QR Code saved successfully")

# GUI Setup
root = tk.Tk()
root.title("QR Code Generator")

entry = tk.Entry(root, width=40)
entry.pack(pady=10)

generate_btn = tk.Button(root, text="Generate QR Code", command=generate_qr)
generate_btn.pack()

qr_label = tk.Label(root)
qr_label.pack()

save_btn = tk.Button(root, text="Save QR Code", command=save_qr)
save_btn.pack()

root.mainloop()
```
