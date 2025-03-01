# chula_eng

import tkinter as tk
import random

# Thai consonants and their names
thai_consonants = [
    ("ก", "gor kai"), ("ข", "khor khai"), ("ค", "khor khwai"),
    ("ง", "ngor ngu"), ("จ", "jor jan"), ("ฉ", "chor ching"),
    ("ช", "chor chang"), ("ซ", "sor so"), ("ญ", "yor ying"),
]

class FlashcardApp:
    def __init__(self, root):
        self.root = root
        self.root.title("Thai Consonant Flashcards")
        
        self.card_frame = tk.Frame(root)
        self.card_frame.pack(pady=50)
        
        self.consonant_label = tk.Label(self.card_frame, text="", font=("Arial", 100))
        self.consonant_label.pack()
        
        self.name_label = tk.Label(self.card_frame, text="", font=("Arial", 24))
        self.name_label.pack()
        
        self.flip_button = tk.Button(root, text="Flip", command=self.flip_card, font=("Arial", 18))
        self.flip_button.pack(pady=10)
        
        self.next_button = tk.Button(root, text="Next", command=self.next_card, font=("Arial", 18))
        self.next_button.pack()
        
        self.current_card = None
        self.next_card()
    
    def next_card(self):
        self.current_card = random.choice(thai_consonants)
        self.consonant_label.config(text=self.current_card[0])
        self.name_label.config(text="")
    
    def flip_card(self):
        if self.current_card:
            self.name_label.config(text=self.current_card[1])

if __name__ == "__main__":
    root = tk.Tk()
    app = FlashcardApp(root)
    root.mainloop()