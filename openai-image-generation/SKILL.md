# OpenAI Image Generation Skill

Bu skill OpenAI Images API'sini kullanarak metin prompt'larından görsel üretir.

## Gereksinimler

- OPENAI_API_KEY environment variable
- Python3 ve requests kütüphanesi

## Desteklenen Modeller

### GPT Image Models
- `gpt-image-1` (varsayılan)
- `gpt-image-1-mini` 
- `gpt-image-1.5`

**Özellikler:**
- Boyutlar: 1024x1024, 1536x1024, 1024x1536, auto
- Kalite: auto, high, medium, low (varsayılan: high)
- Ek parametreler: background (transparent/opaque/auto), output-format (png/jpeg/webp)

### DALL-E 3
- Model: `dall-e-3`
- Boyutlar: 1024x1024, 1792x1024, 1024x1792
- Kalite: hd, standard (varsayılan: standard)  
- Stil: vivid, natural
- Not: Tek seferde sadece 1 görsel üretir

### DALL-E 2
- Model: `dall-e-2`
- Boyutlar: 256x256, 512x512, 1024x1024
- Kalite: standard

## Kullanım

### Temel Komutlar

```bash
# GPT image model ile basit üretim
python3 gen.py --prompt "ultra-detailed studio photo of a lobster astronaut" --count 4

# DALL-E 3 ile yüksek kalite
python3 gen.py --model dall-e-3 --quality hd --size 1792x1024 --style vivid --prompt "serene mountain landscape"

# GPT model ile özel parametreler
python3 gen.py --model gpt-image-1.5 --size 1536x1024 --quality high --background transparent --output-format webp
```

### Parametre Açıklamaları

- `--model`: Kullanılacak model (gpt-image-1, dall-e-3, dall-e-2)
- `--prompt`: Görsel için açıklama metni
- `--count`: Üretilecek görsel sayısı (DALL-E 3 için maksimum 1)
- `--size`: Görsel boyutu (model bazında değişir)
- `--quality`: Kalite seviyesi
- `--style`: Stil (sadece DALL-E 3 için)
- `--background`: Arkaplan tipi (sadece GPT modelleri için)
- `--output-format`: Çıktı formatı (sadece GPT modelleri için)

### Örnek Python Kodu

```python
import requests
import os
import json
from datetime import datetime

def generate_image(prompt, model="gpt-image-1", size="1024x1024", quality="high", count=1):
    """
    OpenAI Images API ile görsel üret
    """
    
    api_key = os.getenv('OPENAI_API_KEY')
    if not api_key:
        raise ValueError("OPENAI_API_KEY environment variable gerekli")
    
    headers = {
        'Authorization': f'Bearer {api_key}',
        'Content-Type': 'application/json'
    }
    
    # Model bazında parametreleri ayarla
    data = {
        'model': model,
        'prompt': prompt,
        'n': min(count, 1 if model == 'dall-e-3' else count),
        'size': size
    }
    
    # Model-özel parametreler
    if model.startswith('gpt-image'):
        data['quality'] = quality
    elif model == 'dall-e-3':
        data['quality'] = quality if quality in ['hd', 'standard'] else 'standard'
    
    response = requests.post(
        'https://api.openai.com/v1/images/generations',
        headers=headers,
        json=data
    )
    
    if response.status_code != 200:
        raise Exception(f"API hatası: {response.status_code} - {response.text}")
    
    result = response.json()
    image_urls = [item['url'] for item in result['data']]
    
    return image_urls

# Kullanım örneği
if __name__ == "__main__":
    try:
        urls = generate_image(
            prompt="A beautiful sunset over mountains, photorealistic",
            model="gpt-image-1",
            size="1536x1024", 
            quality="high",
            count=2
        )
        
        print("Üretilen görseller:")
        for i, url in enumerate(urls, 1):
            print(f"{i}. {url}")
            
    except Exception as e:
        print(f"Hata: {e}")
```

## İpuçları

1. **Prompt Yazımı**: Detaylı ve açık promptlar daha iyi sonuçlar verir
2. **Model Seçimi**: 
   - Hız için: gpt-image-1-mini
   - Kalite için: gpt-image-1.5 veya dall-e-3
   - Çoklu üretim için: GPT modelleri
3. **Boyut Seçimi**: Kullanım amacına göre boyut seç (sosyal medya, baskı, vs.)
4. **Maliyet**: DALL-E 3 daha pahalı, GPT modelleri daha ekonomik

## Hata Giderme

- API key kontrolü: `echo $OPENAI_API_KEY`
- Network bağlantısı kontrolü
- Rate limit: Çok hızlı istek gönderme
- Invalid size: Model-uyumlu boyut kullan