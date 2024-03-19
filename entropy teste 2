import numpy as np
from collections import Counter
import math

# Gerar dados de atividade neuronal simulados
num_neurons = 100  # Número de neurônios
num_time_steps = 1000  # Número de passos de tempo
spike_probability = 0.1  # Probabilidade de um neurônio disparar em um determinado passo de tempo

# Gerar dados de atividade neuronal simulados
neural_data = np.random.choice([0, 1], size=(num_neurons, num_time_steps), p=[1 - spike_probability, spike_probability])

# Função para calcular a entropia de Shannon de uma série de dados
def shannon_entropy(data):
    freqs = Counter(data)
    entropy = 0.0
    total_values = len(data)
    for freq in freqs.values():
        probability = freq / total_values
        entropy -= probability * math.log2(probability)
    return entropy

# Calcular a entropia de Shannon para cada neurônio
entropies = []
for neuron_data in neural_data:
    entropy = shannon_entropy(neuron_data)
    entropies.append(entropy)

# Exibir a entropia média e a entropia máxima entre os neurônios
print("Entropia média:", np.mean(entropies))
print("Entropia máxima:", np.max(entropies))
