## Transporte Público Inteligente

Plataforma que gestiona una flota de buses inteligentes. Los usuarios consultan tiempos de 
llegada (ETA) en tiempo real y recargan tarjetas electrónicas. Cada bus dispone de un 
dispositivo embarcado (Bus Device) y un Sidecar que envían telemetría y logs a la nube. El 
sistema integra APIs externas (como GPS) a través de un Ambassador Proxy para garantizar 
solidez.

Objetivo: Ofrecer a pasajeros y operadores información en tiempo real sobre ubicaciones, 
tiempos de llegada y estado operativo de la flota, además de permitir recargas electrónicas. 