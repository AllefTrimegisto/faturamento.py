
3) Dado um vetor que guarda o valor de faturamento diário de uma distribuidora, faça um programa, na linguagem que desejar, que calcule e retorne:
	• O menor valor de faturamento ocorrido em um dia do mês;
	• O maior valor de faturamento ocorrido em um dia do mês;
	• Número de dias no mês em que o valor de faturamento diário foi superior à média mensal.

IMPORTANTE:
	a) Usar o json ou xml disponível como fonte dos dados do faturamento mensal;
	b) Podem existir dias sem faturamento, como nos finais de semana e feriados. Estes dias devem ser ignorados no cálculo da média;
  
  import json

# Lê o vetor de faturamento diário a partir de um arquivo JSON
with open('faturamento.json', 'r') as file:
    faturamento_diario = json.load(file)

# Inicializa as variáveis para cálculo do menor e maior valor
menor_valor = faturamento_diario[0]
maior_valor = faturamento_diario[0]

# Inicializa as variáveis para cálculo da média mensal
soma_dias_uteis = 0
num_dias_uteis = 0

# Percorre o vetor de faturamento diário
for valor in faturamento_diario:
    # Calcula o menor valor
    if valor < menor_valor:
        menor_valor = valor
    # Calcula o maior valor
    if valor > maior_valor:
        maior_valor = valor
    # Calcula a média mensal considerando apenas dias úteis
    if valor > 0:
        soma_dias_uteis += valor
        num_dias_uteis += 1

media_mensal = soma_dias_uteis / num_dias_uteis

# Inicializa a variável para cálculo do número de dias com faturamento acima da média
num_dias_acima_da_media = 0

# Percorre o vetor de faturamento diário novamente
for valor in faturamento_diario:
    # Conta os dias em que o faturamento foi maior que a média mensal
    if valor > media_mensal:
        num_dias_acima_da_media += 1

# Imprime os resultados
print(f"Menor valor de faturamento diário: R$ {menor_valor:.2f}")
print(f"Maior valor de faturamento diário: R$ {maior_valor:.2f}")
print(f"Número de dias com faturamento acima da média mensal: {num_dias_acima_da_media}")

