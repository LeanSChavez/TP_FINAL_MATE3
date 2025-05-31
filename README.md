# TP_FINAL_MATE3

Este trabajo esta basado en un **DataSet** de 50 millones de manos de blackjack simuladas. Dicho dataset fue reducido realizando el siguiente codigo:

import pandas as pd
import random

ruta_csv = 'blackjack_simulator.csv'
n_muestra = 100_000
total_filas = 50_000_000  

# Cargar una muestra sin leer todo el archivo
muestra = pd.read_csv(
    ruta_csv,
    skiprows=lambda i: i > 0 and random.random() > (n_muestra / total_filas) 
)

# Guardar en un nuevo CSV
muestra.to_csv('muestra_100k.csv', index=False)

Lo que hace es darte una muestra aleatoria del dataset evitando cargar todos los datos, que ademas subirlo a git resultaba inviable

Con la muestra de datos ya reducida, comenzamos a modelarla para poder empezar una red neuronal que, segun una mano de blackjack y una carta que muestra el dealer, te dice que accion te recomienda hacer, si pedir una carta mas, o quedarte.