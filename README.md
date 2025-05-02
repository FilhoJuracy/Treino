# Treino
Calculo da Dosagem de Floculante
def converter_volume_para_litros(volume, unidade):
    """
    Converte volume para litros.
    unidade: 'mL', 'L', 'm3'
    """
    if unidade == 'mL':
        return volume / 1000
    elif unidade == 'L':
        return volume
    elif unidade == 'm3':
        return volume * 1000
    else:
        raise ValueError("Unidade inválida. Use 'mL', 'L' ou 'm3'.")

def calcular_dosagem(volume, unidade_volume, solidos_gl, concentracao_poly_percent, massa_polymer_g):
    """
    Calcula a dosagem de polímero em g/t
    """
    volume_litros = converter_volume_para_litros(volume, unidade_volume)
    massa_solidos_total = solidos_gl * volume_litros  # em gramas
    dosagem = (massa_polymer_g / massa_solidos_total) * 1_000_000  # g/t
    return dosagem

def main():
    print("--- Calculadora de Dosagem de Polímero (g/t) ---")
    volume = float(input("Informe o volume de lama: "))
    unidade = input("Informe a unidade (mL, L ou m3): ").strip()
    solidos = float(input("Informe a concentração de sólidos (g/L): "))
    concentracao_poly_percent = float(input("Informe a concentração do polímero (%): "))
    
    massa_polymer = float(input("Informe a massa de polímero adicionada (em gramas): "))

    dosagem = calcular_dosagem(volume, unidade, solidos, concentracao_poly_percent, massa_polymer)
    print(f"\nResultado: Dosagem de polímero = {dosagem:.2f} g/t")

if __name__ == "__main__":
    main()
