The not virus


the code 
import tkinter as tk
import os
messages = [
    "Привет я вирус",
    "мне скучьно",
    "сам удали важные вещи и кинь свои пароли",
    "вот ошибка для вида",
    "Пока хорошего дня",
]
CHECK_PATH = "A:/chicatilo"
root = tk.Tk()
root.title("Уведомления")
root.geometry("400x200")
label = tk.Label(root, text="", font=("Arial", 14), wraplength=380, justify="center")
label.pack(expand=True)
index = 0  
def check_folder():
    """Проверяет, существует ли папка A:/chicatilo"""
    if os.path.isdir(CHECK_PATH):
        return f"Папка найдена:\n{CHECK_PATH}"
    else:
        return f"Папка НЕ найдена:\n{CHECK_PATH}"
def show_message():
    global index
    if index < len(messages):
        if index == 3:
            result = check_folder()
            label.config(text=f"{messages[index]}\n\n{result}")
        else:
            label.config(text=messages[index])
        index += 1
        root.after(3000, show_message)
    else:
        root.destroy()
show_message()
root.mainloop()
