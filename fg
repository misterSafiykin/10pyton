import tkinter as tk


# ---------------- GAME VARIABLES ----------------

bomb = 100
score = 0
game_started = False


# ---------------- WINDOW ----------------

root = tk.Tk()
root.title("Bomb Clicker")
root.geometry("600x600+700+200")
root.resizable(False, False)

try:
    root.iconbitmap("favicon.ico")
except:
    pass


# ---------------- LABELS ----------------

label_1 = tk.Label(
    root,
    text="PRESS ENTER TO START",
    font=("Comic Sans MS", 18, "bold")
)
label_1.pack(pady=15)


fuse_label = tk.Label(
    root,
    text="Fuse: 100",
    font=("Comic Sans MS", 14)
)
fuse_label.pack()


score_label = tk.Label(
    root,
    text="Score: 0",
    font=("Comic Sans MS", 14)
)
score_label.pack(pady=5)


# ---------------- BOMB IMAGES ----------------

img_1 = tk.PhotoImage(file="bomb_1.png").subsample(3, 3)
img_2 = tk.PhotoImage(file="bomb_2.png").subsample(3, 3)
img_3 = tk.PhotoImage(file="bomb_3.png").subsample(3, 3)
img_4 = tk.PhotoImage(file="bomb_4.png").subsample(3, 3)


bomb_label = tk.Label(
    root,
    image=img_1,
    cursor="hand2"
)

bomb_label.pack(pady=30)


# ---------------- FUNCTIONS ----------------

def update_display():
    fuse_label.config(text=f"Fuse: {bomb}")
    score_label.config(text=f"Score: {score}")


def change_bomb_image():

    if bomb > 75:
        bomb_label.config(image=img_1)

    elif bomb > 50:
        bomb_label.config(image=img_2)

    elif bomb > 25:
        bomb_label.config(image=img_3)

    else:
        bomb_label.config(image=img_4)


def click_bomb(event=None):

    global bomb
    global score

    if game_started == False:
        return

    score += 1
    bomb -= 1

    update_display()
    change_bomb_image()

    if bomb <= 0:
        game_over()


def start_game(event=None):

    global bomb
    global score
    global game_started

    bomb = 100
    score = 0
    game_started = True

    label_1.config(text="CLICK THE BOMB!")

    bomb_label.config(image=img_1)

    update_display()

    # Повертаємо фокус на головне вікно
    root.focus_set()


def game_over():

    global game_started

    game_started = False

    label_1.config(text="BOOM! GAME OVER!")
    bomb_label.config(image=img_4)


def restart_game():

    start_game()


# ---------------- RESTART BUTTON ----------------

restart_button = tk.Button(
    root,
    text="RESTART",
    font=("Comic Sans MS", 12),
    command=restart_game
)

restart_button.pack(pady=10)


# ---------------- BOMB CLICK ----------------

bomb_label.bind(
    "<Button-1>",
    click_bomb
)


# ---------------- ENTER KEY ----------------

# Enter
root.bind(
    "<Return>",
    start_game
)

# Enter на цифровій клавіатурі
root.bind(
    "<KP_Enter>",
    start_game
)


# ---------------- KEYBOARD FOCUS ----------------

root.focus_set()


# ---------------- RUN ----------------

root.mainloop()
