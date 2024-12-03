## Plano Detalhado para Transformação do Vídeo

### **Objetivo**

1. Inverter a imagem no eixo horizontal a cada 20 segundos.
2. Diminuir o som de forma gradativa a cada 30 segundos, garantindo que os últimos 10 segundos fiquem em silêncio.
3. Após o primeiro minuto (60 segundos), cortar um trecho entre os segundos 60 e 80.
4. Inserir o trecho cortado ao final do vídeo.

### **Etapas**

#### **1. Inversão no Eixo Horizontal a Cada 20 Segundos**
- **Técnica**: Divisão do vídeo em clipes de 20 segundos.
- **Implementação**:
  - Usada a função `subclip` para dividir o vídeo em intervalos de 20 segundos.
  - Aplicado `vfx.mirror_x` aos clipes alternados para inverter a imagem horizontalmente.

#### **2. Redução Gradativa do Som**
- **Técnica**: Ajuste de volume baseado no tempo do clipe.
- **Implementação**:
  - Usada a função `volumex` com uma função personalizada para reduzir o volume em 10% a cada 30 segundos.
  - Garantir que o volume fique completamente em silêncio nos últimos 10 segundos.

#### **3. Corte do Trecho Entre 60 e 80 Segundos**
- **Técnica**: Extração de subclipe.
- **Implementação**:
  - Usada a função `subclip` para extrair o trecho desejado (60 a 80 segundos).

#### **4. Reorganização do Vídeo**
- **Técnica**: Concatenação de clipes.
- **Implementação**:
  - Usada `concatenate_videoclips` para reorganizar as partes do vídeo na ordem desejada:
    - Os primeiros 60 segundos.
    - O trecho após 80 segundos.
    - O trecho cortado (60 a 80 segundos).

#### **5. Salvamento do Vídeo Final**
- **Técnica**: Exportação com codecs adequados.
- **Implementação**:
  - Usada `write_videofile` para salvar o vídeo final com os codecs `libx264` e `aac`.
