# 📊 Documentação de Padrões de Candlestick

Esta documentação cobre todos os padrões de candlestick suportados pelo **pandas_ta** e **TA-Lib**, incluindo suas interpretações, ações recomendadas e regras de confirmação.

---

## **Lista Completa de Padrões de Candlestick**

| **Nome do Padrão**                      | **Significado**                     | **Ação Recomendada** | **Regra de Confirmação** |
|----------------------------------------|---------------------------------|----------------------|--------------------------|
| **CDL2CROWS** (Two Crows)             | Reversão de baixa             | ❌ Vender            | Volume alto no candle de confirmação |
| **CDL3BLACKCROWS** (Three Black Crows)| Forte reversão de baixa       | ❌ Vender            | Confirmar com RSI abaixo de 50 e volume crescente |
| **CDL3INSIDE** (Three Inside Up/Down) | Reversão confirmada           | 🔄 Confirmar         | O terceiro candle precisa romper a máxima/mínima do segundo candle |
| **CDL3LINESTRIKE** (Three-Line Strike)| Continuidade da tendência      | 🔄 Confirmar         | O candle seguinte precisa continuar na mesma direção |
| **CDL3OUTSIDE** (Three Outside Up/Down)| Reversão confirmada          | ✅ Comprar ou ❌ Vender | O fechamento precisa estar acima/abaixo da máxima/mínima do segundo candle |
| **CDLENGULFING** (Engulfing)          | Reversão confirmada           | ✅ Comprar ou ❌ Vender | O candle engolido deve ter volume menor que o engolfador |
| **CDLDOJI** (Doji)                    | Indecisão no mercado         | 🔄 Confirmar         | Confirmação na próxima vela com rompimento da máxima/mínima |
| **CDLHAMMER** (Hammer)                | Sinal de reversão bullish     | ✅ Comprar           | Precisa de candle seguinte fechando acima da máxima do Hammer |
| **CDLHANGINGMAN** (Hanging Man)       | Indica possível reversão bearish | ❌ Vender            | Confirmar com candle seguinte fechando abaixo da mínima |
| **CDLMARUBOZU** (Marubozu)            | Confirmação da tendência    | ✅ Comprar ou ❌ Vender | Volume acima da média fortalece o sinal |
| **CDLSHOOTINGSTAR** (Shooting Star)   | Forte reversão bearish        | ❌ Vender            | Precisa de candle seguinte confirmando queda |

---

## 📌 **Como Confirmar os Padrões**
Se a **Ação Recomendada** for **🔄 Confirmar**, siga estas regras:

1️⃣ **Procure um candle forte na direção esperada** após o padrão.  
2️⃣ **Cheque o volume**: Volume alto aumenta a confiabilidade do sinal.  
3️⃣ **Use indicadores de suporte**:
   - RSI **abaixo de 30** → confirma compras  
   - RSI **acima de 70** → confirma vendas  
   - Médias móveis → Padrões são mais confiáveis se a reversão ocorrer próximo delas.  
4️⃣ **Verifique suporte/resistência**: Padrões são mais confiáveis se aparecem em zonas importantes.  

---

## 📌 **Exemplo de Uso com pandas_ta**

```python
import pandas as pd
import pandas_ta as ta

# Criar um DataFrame com preços fictícios
data = {
    "open": [100, 102, 101, 105, 104],
    "high": [103, 106, 104, 108, 107],
    "low": [99, 101, 100, 103, 102],
    "close": [102, 104, 103, 107, 106]
}
df = pd.DataFrame(data)

# Detectar padrões de candles
df["doji"] = df.ta.cdl_pattern(name="doji")
df["engulfing"] = df.ta.cdl_pattern(name="engulfing")
df["hammer"] = df.ta.cdl_pattern(name="hammer")

print(df)
```

---

## 📢 **Conclusão**
- ✅ Agora você tem **todos os padrões** suportados pelo `pandas_ta`!  
- 🚀 Combine com **outros indicadores** para aumentar a precisão.  
- ⚠ **Gerencie o risco**: não opere apenas com base em um único sinal.  

