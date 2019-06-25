# Análise de Desempenho da Google Cloud Vision API

Análise de Desempenho da Google Vision API  em Leitura Robusta de Textos Provenientes de Imagens Naturais

## Objetivo

O objetivo deste trabalho é analisar o desempenho do Google Cloud Vision na sua ferramenta de detecção de textos utilizando imagens naturais e avaliando sua acurácia por meio dos resultados das competições do ICDAR.

## Competição

Uma das competições que fizeram parte do evento ICDAR 2017, foi a Robust Reading Challenge on COCO-Text, um desafio que tem como ambiente de estudo, imagens naturais de textos (textos em placas, camisetas, veículos, casas, etc). Este desafio aborda a necessidade de quantificar e acompanhar o progresso no domínio da compreensão do texto em ambientes irrestritos focado em textos da língua Inglesa.

### Tarefa

O Robust Reading Challenge on COCO-Text organizado em 2017 com Reconhecimento de palavras (Cropped word recognition): Detectar e prover o conteúdo em termos de texto (transcrição) dentro dos limites de localizados numa imagem.

## Dataset

O `dataset` em questão, `Cropped words dataset` exclusivo para o trabalho, possui as seguintes características:

- Apenas as palavras legíveis e em inglês do `dataset` `COCO-Text` são utilizadas;
- Apenas palavras com mais de 3 caracteres compõe o `dataset`;
- Todas as imagens possuem 2 `pixels` de borda para os limites do texto na imagem;
- O formato esperado é um arquivo .txt com uma linha por palavra detectada em cada imagem, separada por `,` no formato: `nome_do_arquivo, transcrição`;
- As transcrições são no formado `UTF-8`;
- 9.837 imagens de teste. Imagens essas, que farão parte do conjunto de submissão para a competição.

## Ferramenta

A Aplicação consiste nu notebook `jupyter` e implementada na linguagem de programação `Python` que faz um percurso sobre todas as imagens do conjunto de testes para a submissão. 

### Métodos
- `get_date()` (retorna ano, mês, dia, hora e minuto atual);
- `image_to_json_annotations(GOOGLE_API_KEY, image_filename)` (processa todos as imagens e organiza suas anotações em arquivo `.json`);
- `estimate_noise(image_path)` (faz a estimativa do nível de ruído da imagem);
- `denoise_tv(filename)` (remove os ruídos da imagem);
- `processar_lote_imagens(IMAGES_DIR, remover_ruido=False)` (processa em lote, as imagens de uma pasta, removendo (ou não) os ruídos dela);
- `json_to_data(json_file)` (conversão de `json` para `dataframe`);
- `gera_resultados_submissao(OUTPUT_RESULT_FOLDER, RESPONSE_DIR)` (cria arquivo de texto pronto para submissão na competição).

### Dependências
Dependências necessárias para a execução da aplicação.
- `pip install requests`
- `pip install opencv-python`
- `pip install scikit-image`
- `pip install pandas`
- `pip install numpy`


