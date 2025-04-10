## Equipe reponsável: Diego, Clevison, Luiz Henrique e Joaquim 

## Projeto de controle de luminosidade de uma estufa de planta ornamental

<p> Plantas ornamentais são espécies cultivadas com o principal objetivo de embelezar ambientes, sejam eles internos ou externos. Elas são apreciadas por suas cores, formas, texturas e perfumes, e incluem uma grande variedade de tipos, como flores, arbustos, árvores, trepadeiras e até mesmo suculentas e cactos.</p>

<p> Essas plantas desempenham um papel importante na decoração de jardins, praças, varandas, escritórios e residências, trazendo vida, frescor e sofisticação aos espaços. Além da estética, muitas também contribuem para a melhoria da qualidade do ar, promovem bem-estar e proporcionam um contato mais próximo com a natureza.</p> 
<p> No ano de 2009 a floricultura movimentou aproximadamente 750
milhões de reais e no ano seguinte esse valor foi próximo de 825 milhões de
reais (ICEPA, 2010). Esse crescimento é causado principalmente
pelo aumento da renda dos brasileiros, o acesso mais fácil as plantas e o
avanço das tecnologias usadas nessa atividade (IBRAFLOR, 2011).</p>


### Motivação do projeto: Controle de Luminosidade em uma Estufa para Plantas Ornamentais

<p> O cultivo de plantas ornamentais exige atenção cuidadosa a diversos fatores ambientais, sendo a luminosidade um dos mais determinantes para o crescimento saudável e o desenvolvimento estético dessas espécies. Cada planta possui necessidades específicas de luz, e o controle inadequado pode comprometer sua cor, forma e até sua sobrevivência. </p>
<p> Pensando nisso, este projeto visa desenvolver um sistema eficiente de controle de luminosidade em estufas, que permita criar um ambiente ideal para o cultivo de diferentes tipos de plantas ornamentais. Através da automação e monitoramento contínuo da intensidade luminosa, buscamos oferecer às plantas as condições ideais para que expressem todo o seu potencial ornamental. </p>
<p> O projeto prático teve se início usando o site Tinkercad, para desenvolvimento e progamação simulando ambientes reais, abaixo está listado os componentes usados no projeto.</p>

 **Componentes usados:**

* Arduino UNO
* Protoboard
* 3 resistores de 220Ω
* 1 resistor de 10kΩ
* 3 leds, sendo 1 verde, 1 amarelo e 1 vermelho
* 1 buzzer 
* 1 fotoresistor LDR 

``FOTO PROJETO``
![Foto do projeto](img02.png)


**Código do projeto:**
```const int pinoldr = A0; 
const int pinoverm = 2; 
const int pinoama = 3; 
const int pinoverd = 4; 
const int pinobuzzer = 5; 

int lumimax = 0; 
int valorldr = 0; 

void setup() {
  Serial.begin(9600);
  pinMode(pinoverm, OUTPUT);
  pinMode(pinoama, OUTPUT);
  pinMode(pinoverd, OUTPUT);
  pinMode(pinobuzzer, OUTPUT);
  
  
  Serial.println("Calibrando LDR... Aguarde.");
  for (int i = 0; i < 100; i++) {
    valorldr = analogRead(pinoverm);
    if (valorldr > lumimax) {
      lumimax = valorldr;
    }
    delay(100);
  }
  Serial.print("Luminosidade maxima: ");
  Serial.println(lumimax);
}

void loop() {
  valorldr = analogRead(pinoldr);
  Serial.print("Luminosidade atual: ");
  Serial.println(valorldr);
  
  if (valorldr >= 0.8 * lumimax) { 
    digitalWrite(pinoverm, HIGH);
    digitalWrite(pinoama, LOW);
    digitalWrite(pinoverd, LOW);
    for (int i = 0; i < 3; i++) {
      tone(pinobuzzer, 1000, 200); 
      delay(300);
    }
  } else if (valorldr >= 0.5 * lumimax) { 
    digitalWrite(pinoverm, LOW);
    digitalWrite(pinoama, HIGH);
    digitalWrite(pinoverd, LOW);
    for (int i = 0; i < 2; i++) {
      tone(pinobuzzer, 1000, 200); 
      delay(300);
    }
  } else if (valorldr < 0.5 * lumimax) { 
    digitalWrite(pinoverm, LOW);
    digitalWrite(pinoama, LOW);
    digitalWrite(pinoverd, HIGH);
    tone(pinobuzzer, 1000, 200); 
  }
  
  delay(1000);
}
```
**Artigos embasados como referência:** <br>
Produção e Comercialização de Plantas
Ornamentais na Empresa Fazenda do Jardim - Morgana Tuzzi (2011) <br>
Link:https://repositorio.ufsc.br/xmlui/bitstream/handle/123456789/25460/ragr245.pdf?sequence=1&isAllowed=y

Utilização do Ciclo PDCA para Desenvolvimento de uma Estufa Agrícola Automatizada - Vitor Abel Monteiro Alves (2019) <br>
Link:https://d1wqtxts1xzle7.cloudfront.net/63151155/2019_capitulo_Estufa20200430-92939-z0vhob-libre.pdf?1588275753=&response-content-disposition=inline%3B+filename%3DCapitulo_8_Utilizacao_do_ciclo_PDCA_para.pdf&Expires=1744243485&Signature=UXLrm5XuD-aP-h09jteV6Kh8gEYWkRMOmLozPufqfpt2NoOoC2AwntUG3pcGgJoJu-bh1ovVYs1lK3Wz5G6R~Gl5BkPQD9SECy~3mAVqQJ-y4JGIzOYvLHLvwYuuSizkqFf-kw2J-DxUXY4NiaqKs0PGF9UknKNTXeJi5jV9j5bWWXcyrqX~Fo4pC-rUsfOIr~ulRbjZLowmiOpiUytN~GfLlcwuXYqC7tj58M~1UjG5QzF9u0movZCDFUr-~UVSmfXXe~uYh-TylIbQVcokkCSO2W-lyYuXT-9rTyGk99957AMrDxUaD1q4S6v~AdhUzu8~uNZqcL--~x4f8Ih9Kw__&Key-Pair-Id=APKAJLOHF5GGSLRBV4ZA

Cadeia de produção, comercialização e logística de sementes, mudas e plantas ornamentais no Estado de São Paulo - Douglas Brand (2014) <br>
Link: https://lume.ufrgs.br/handle/10183/268100 
<br>
Link para o Tinkercad: https://www.tinkercad.com/things/43vhzp1UEHJ/editel?returnTo=%2Fdashboard



 

