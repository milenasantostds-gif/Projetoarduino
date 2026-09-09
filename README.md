#  Luz Automática com Arduino e Sensor LDR

Este é um projeto simples e funcional de automação residencial utilizando a plataforma **Arduino**. O sistema monitora a luminosidade do ambiente através de um sensor **LDR (Resistor Dependente de Luz)** e acende automaticamente um **LED** quando o ambiente fica escuro.

---

##  Componentes Necessários

* 1x Placa **Arduino** (Uno, Nano, Mega, etc.)
* 1x Sensor de Luz **LDR 5mm**
* 1x **LED** (Qualquer cor)
* 1x Resistor de **10kΩ** (para o LDR)
* 1x Resistor de **220Ω** (para o LED)
* 1x Protoboard e Jumpers de conexão

---

##  Esquema de Ligação (Circuito)

Como conectar os componentes na sua placa Arduino:

| Componente           | Pino do Arduino | Observação                                                    |
| :------------------- | :-------------- | :------------------------------------------------------------ |
| **LED (Anodo /+)**   | `Pino 13`       | Conectar em série com o resistor de 220Ω                      |
| **LED (Catodo /-)**  | `GND`           |                                                               |
| **LDR (Terminal 1)** | `VCC (5V)`      |                                                               |
| **LDR (Terminal 2)** | `Pino A0`       | Conectar também ao resistor de 10kΩ ligado ao GND (Pull-Down) |

---

##  Código Fonte

O código lê o valor analógico do LDR e ativa o pino do LED caso a luz ambiente fique abaixo do limite configurado.

```cpp
// Pinos utilizados
int LED = 13;
int LDR = A0;
int valor_LDR;

void setup() {
  pinMode(LED, OUTPUT);
  pinMode(LDR, INPUT);
  Serial.begin(9600); // Inicializa o Monitor Serial
}

void loop() {
  valor_LDR = analogRead(LDR); // Lê o valor do sensor (0 a 1023)
  Serial.println(valor_LDR);    // Exibe o valor no Monitor Serial

  // Ajuste o valor '1000' de acordo com a luminosidade do seu ambiente
  if (valor_LDR > 1000) {
    digitalWrite(LED, HIGH);   // Acende o LED
    delay(1000);
  } else {
    digitalWrite(LED, LOW);    // Apaga o LED
    delay(1000);
  }
}
```

---

##  Como Executar o Projeto

1. Baixe e instale a Arduino IDE.
2. Conecte sua placa Arduino ao computador via USB.
3. Copie o código acima e cole na IDE.
4. Selecione a placa e a porta corretas no menu **Ferramentas**.
5. Clique em **Carregar (Upload)**.
6. Abra o **Monitor Serial** (9600 bps) para acompanhar as leituras do LDR em tempo real.

---

## 🔧 Possíveis Melhorias

* [ ] Substituir o LED por um **Módulo Relé** para controlar lâmpadas reais de 110V/220V.
* [ ] Criar uma calibração automática para o valor de corte do LDR.
* [ ] Adicionar um display LCD para mostrar o nível de luz atual.

---

##  Integrantes do Projeto

Este projeto foi desenvolvido por:

* 👨‍💻 **João Pedro**
* 👩‍💻 **Milena**
* 👩‍💻 **Maria Vitória**

---

