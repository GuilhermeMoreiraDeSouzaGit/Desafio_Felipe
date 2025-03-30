import customtkinter as ctk
from tkinter import messagebox

def calcular_rank(pdl_atual):
    if pdl_atual < 10:
        return "Ferro"
    elif pdl_atual <= 20:
        return "Bronze"
    elif pdl_atual <= 50:
        return "Prata"
    elif pdl_atual <= 80:
        return "Ouro"
    elif pdl_atual <= 90:
        return "Diamante"
    elif pdl_atual <= 100:
        return "Lendário"
    else:
        return "Imortal"

def calcular_pdl(pdl_atual, pdl_por_partida, ganhou):
    # Garantir que o valor de PDL não ultrapasse 100
    pdl_maximo = 100
    if pdl_por_partida > pdl_maximo:
        pdl_por_partida = pdl_maximo
    
    if ganhou:
        return pdl_atual + pdl_por_partida if pdl_atual + pdl_por_partida <= pdl_maximo else pdl_maximo
    return pdl_atual - pdl_por_partida if pdl_atual - pdl_por_partida >= 0 else 0

def registrar_resultado(ganhou):
    global pdl_atual
    try:
        # Validação para garantir que o valor inserido seja um número inteiro e não negativo
        pdl_por_partida = entry_pdl.get()
        if not pdl_por_partida.isdigit() or int(pdl_por_partida) < 0:
            raise ValueError("Por favor, insira um número válido e não negativo para PDL.")

        pdl_por_partida = int(pdl_por_partida)
        pdl_atual = calcular_pdl(pdl_atual, pdl_por_partida, ganhou)
        
        nivel = calcular_rank(pdl_atual)
        
        # Atualizar o texto do label usando configure
        label_resultado.configure(text=f"PDL: {pdl_atual} | Rank: {nivel}")
    except ValueError as ve:
        messagebox.showerror("Erro", str(ve))

def sair():
    root.destroy()

# Configuração da interface gráfica usando customtkinter
root = ctk.CTk()
root.title("Calculadora de Partidas Rankeadas")
root.geometry("400x300")

pdl_atual = 0

# Label para entrada de PDL
label_pdl = ctk.CTkLabel(root, text="Digite a quantidade de PDL por partida:")
label_pdl.pack(pady=10)

# Entry para inserir o valor de PDL
entry_pdl = ctk.CTkEntry(root)
entry_pdl.pack(pady=10)

# Botão de Vitória
btn_vitoria = ctk.CTkButton(root, text="Registrar Vitória", command=lambda: registrar_resultado(True))
btn_vitoria.pack(pady=5)

# Botão de Derrota
btn_derrota = ctk.CTkButton(root, text="Registrar Derrota", command=lambda: registrar_resultado(False))
btn_derrota.pack(pady=5)

# Label para exibir o resultado
label_resultado = ctk.CTkLabel(root, text="PDL: 0 | Rank: Ferro")
label_resultado.pack(pady=20)

# Botão para sair
btn_sair = ctk.CTkButton(root, text="Sair", command=sair)
btn_sair.pack(pady=10)

root.mainloop()
