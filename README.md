jogo animação

import tkinter as tk
from PIL import Image, ImageTk

# Criar a janela
janela = tk.Tk()
janela.title("Animação")
janela.geometry("600x300")

# Carregar a imagem
imagem = Image.open("carta A.jfif")  # Substitua pelo nome da sua imagem
imagem = imagem.resize((100, 150))  # Redimensiona
imagem_tk = ImageTk.PhotoImage(imagem)

# Criar um Canvas (área onde desenhamos a imagem)
canvas = tk.Canvas(janela, width=600, height=300, bg="white")
canvas.pack()

# Adicionar a imagem no canvas
imagem_id = canvas.create_image(0, 150, anchor=tk.NW, image=imagem_tk)

# Função para mover a imagem
pos_x = 0
def animar():
    global pos_x
    pos_x += 10  # valor da velocidade
    if pos_x <= 600:
        canvas.coords(imagem_id, pos_x, 150)
        janela.after(50, animar)  # chama a função de novo depois de 50ms

# Iniciar a animação
animar()

# Rodar a janela
janela.mainloop()
