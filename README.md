# Análise de Notícias do Ministério da Saúde

Utilizamos o site do MInistério da Saúde: https://www.gov.br/saude/pt-br/assuntos/noticias?b_start:int=0 para coletar informações acerca das notícias do Ministério da Saúde, percebemos que em cada página continha 15 notícias com o padrão de url: https://www.gov.br/saude/pt-br/assuntos/noticias?b_start:int=p, sendo p a quantidade de notícias acumuladas, ou seja, na primeira página p = 15, na segunda página p = 30, na terceira página p = 45 e assim por diante. Vasculhamos 2100 notícias e coletamos as seguintes informações de cada uma: 

## Detalhes de cada arquivo JSON
informações{
- **URL**: full_url)
- **Título**: {{title}}
- **Descrição**: {{description}}
- **Subtítulo**: {{subtitle}}
- **Categoria**: {{categoria}}
- **Autora**: {{nome_autora}}
- **Data de Publicação**: {{data_formatada}}

}

Os arquivos foram salvo na pasta data.zip. 

Após coletar o dados, fizemos uma análise descritiva:

1. Frequência de notícias por período (outubro-2023 a dezembro 2024) 
2. Top 20 Tags e Subtítulo mais utilizadas nas notícias entre esse período
3. Análises dos subtítulos e autoras mais frequentes neste período
4. Análise das autoras mais frequentes por data
5. Analisamos a Similiridade Textual entre os subtítulos das notícias, com objetivo de encontrar as manchetes com subtítulos parecidos para isto usando a biblioteca TfidfVectorizer do Python que é usada para converter uma coleção de documentos de texto em uma matriz de características. Basicamente, TF-IDF é uma técnica que reflete a importância de uma palavra em um documento em relação a uma coleção de documentos (corpus). Ela é composta por duas partes:

-> *TF (Term Frequency)*: Mede a frequência de uma palavra em um documento.

-> *IDF (Inverse Document Frequency)*: Mede a importância de uma palavra em todo o corpus. Palavras comuns em muitos documentos têm um valor IDF baixo.

5. Depois usamos a vetorização TF-IDF para calcular a similaridade entre os subtítulos com base nas tags, uma inspiração: https://www.kaggle.com/code/doukanelik/content-based-recommendation-system. Apresentamos os subtitulos mais similiares com IMUNIZAÇÃO, RIO GRANDE DO SUL, MALÁRIA, ETC.
6. Por último, analisamos um algortimo baseado na biblioteca spacy que identifica os nomes próprios dos textos, sites que explicam sobre essa biblioteca: https://medium.com/@flaviagaia/desbravando-os-comandos-da-biblioteca-spacy-para-processamento-de-linguagem-natural-19061d5f7586, vale ressaltar que calculamos a similaridade semantica mas usando a biblioteca TfidfVectorizer e usando a similidade por cosseno (da para usar o spacy também, por meio de similarity()), Essa biblioteca é mais usada para identificar tipos de palavras, por exemplo, se ela é verbo, adjetivo, substantivo...  aqui identificamos se ela é substantivo próprio. 
