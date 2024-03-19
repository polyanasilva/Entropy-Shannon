from collections import Counter
import math

def shannon_entropy(data):
    #Aq ele conta a frequencia de cada caractere na string
    freqs = Counter(data)
    # Calcula a entropia de Shan
    entropy = 0.0
    total_caracters = len(data)
    for frq in freqs.values():
        probability = frq / total_caracters
        entropy -= probability * math.log2(probability)
    return entropy

#EXEMPLOOO
texto = 'texto'
entropia = shannon_entropy(texto)
print('Entropia de Shannon: ',entropia)

# A funçao shannon_entropy calcula a entropia de shannon de uma string
# Ela conta a frequecia de cada caractere na string, calcula a probababilidade
# de cada caractere ocorrer e então usa a fórmula da entropia de Shannon para 
# calcular a entropia total da string
