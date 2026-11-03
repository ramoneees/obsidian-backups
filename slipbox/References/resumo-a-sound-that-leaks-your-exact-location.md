---
title: "I discovered a sound that leaks your exact location (and it's everywhere)"
source: https://simonwillison.net/2026/Nov/3/a-sound-that-leaks-your-exact-location/
date: 2026-11-03
tags: [privacidade, osint, seguranca, processamento-de-sinal]
---

Simon Willison linkou um vídeo de OSINT do canal Colsto que beira o absurdo técnico: extrair de um vídeo comum — qualquer vídeo gravado ao ar livre — a localização exata onde foi gravado, usando só o áudio de fundo. O truque: o som quase imperceptível de aviões passando no céu contém o suficiente para te entregar.

A mecânica: as hélices e turbinas produzem um tom que sofre desvio Doppler conforme o avião se aproxima e se afasta. Analisando o espectro do áudio, dá para medir essas curvas Doppler e inferir velocidade, distância e intervalos entre diferentes voos. Cruzando com dados ADS-B públicos (o rastro de quase todo avião civil), o conjunto de curvas funciona como uma impressão digital geométrica — só existe um ponto no mapa onde aquelas trajetórias produzem exatamente aquele som. Localização geolocalizada sem GPS, sem EXIF, sem metadado.

Na discussão no lobste.rs, os comentaristas compararam com a técnica mais velha de ENF analysis (usar o zumbido da rede elétrica de 50/60Hz como marca d'água temporal), mas a versão com aviões é bem mais esperta: funciona em qualquer lugar com céu movimentado e não depende de infraestrutura de grid. A observação de zesterer resume o tema: todo artefato digital carrega entropia suficiente para contar quase tudo sobre sua criação — só está embrulhado em camadas de obfuscação que não sabemos ler.

Implicação prática: a promessa "áudio de fundo é ruído inofensivo" acabou de morrer de novo. Para qualquer um que publica vídeo de operações sensíveis — ou avalia privacidade de fontes — o soundtrack é agora um vetor de vazamento a tratar como metadado de primeira classe.

## Por que importa

- É o gênero de OSINT criativo que muda como você pensa sobre telemetria: dados públicos (ADS-B) viram sensor passivo de localização quando combinados com física de espectro.
- A tese "noise é signal" se aplica direto ao teu stack: logs, telemetria e timestamps carregam mais informação do que a obfuscação sugere — relevante para segurança doméstica e do cluster Olympus.
- Lado prático: qualquer vídeo que você publica (Casa da Cidade, family stuff) pode ser geolocalizado por terceiros com essa técnica — vale revisar o áudio de fundo como superfície de ataque.

## Frases notáveis

> "Even 'noise' is not actually noise: it's a manifestation of the physical environment. It too is a signal, depending on what you're looking for and how cleverly you can isolate it." (comentário de zesterer no lobste.rs)

> "you can take almost imperceptible background noise of planes from a video soundtrack, figure out their Doppler curves, then cross reference them against ADS-B data to find the exact location of the video" (Simon Willison)
