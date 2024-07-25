# Dashboard RH Entrevistas 2019 2020
    cf. youtube [
        https://www.youtube.com/watch?v=r_3XgLA00Mg
    ]

importar dados 
    bd_integrantes
    BD-RH

excluir colunas prescíndiveis

concatenar as tabelas de entrevistas [
    cada entrevista está em sua respectiva planilha [
        cada planilha se refere a um ano específico [
            2019 ou 2020]]] 
    transformar dados e desabilitar 'Habilitar carga' das tabelas 2019 e 2020 

novas medidas 
    Entrevistas[Qtde Funcionarios]
    Entrevistas[qtde_perguntas]
    funcionarios[qtde_cargos]

criar relacionamento entre as tabelas 'entrevista' e 'funcionários'

tela de fundo 
    adicionar os templates 
     
## Seções 

título 
    Painel do Dept. de Recursos Humans referente à  Satisfação dos Funcionários conforme entrevistas efetuados nos anos 2019 e 2020 

### qtde perguntas respondidas  
    criar visual 
        campo 
            qtde_perguntas 
        manter todos os filtros 
        visual 
            score 
    formatar visual
        visual 
            valor do balão
                font size 24  
        geral 
            propriedades 
                tamanho 
                    altura 72
                    largura 210 
            tela de fundo 
                desabilitada 
            ícones de cabeçalho 
                habilitado 
                    default 

### qtde de cargos   
    criar visual 
        campo 
            qtde_cargos  
        manter todos os filtros 
        visual 
            score 
    formatar visual
        visual 
            valor do balão
                font size 24  
        geral 
            propriedades 
                tamanho 
                    altura 72
                    largura 210 
            tela de fundo 
                desabilitada 
            ícones de cabeçalho 
                habilitado 
                    default 

### qtde funcionarios   
    criar nova medida 
        Qtde Funcionario = DISTINCTCOUNT(funcionario[id_integrante]) 
    criar visual 
        campo 
            nova medida {
                Qtde Funcionario
            } 
        manter todos os filtros 
        visual 
            score 
    formatar visual
        visual 
            valor do balão
                font size 24  
        geral 
            propriedades 
                tamanho 
                    altura 72
                    largura 210 
            tela de fundo 
                desabilitada 
            ícones de cabeçalho 
                habilitado 
                    default 

### comparativo de respostas conforme o ano 
    criar visual 
        gráfico de colunas do tipo clusterizado 
            eixo X 
                Entrevistas[Resposta]
            eixo Y
                Entrevistas[qtde_perguntas]
                    título
                        cor #FFFB00
                    barras 
                        entrevista 1 
                            cor #0084FE
                        entrevista 2
                            cor #E1C233
            legenda
                Entrevistas[Entrevista]
        slice [apontar a unidade onde o funcinario trabalha]
            criar visual
                funcionario[Unidade] 
                manter todos os filtros
            formatar visual 
                visual 
                    valores 
                        cor da fonte 
                        tela de fundo 
                            cor #2AF900
                geral 
                    efeitos 
                        tela de fundo 
                            desabilitada 
                    ícones de cabeçalho 
                        habilitado 
        grafico de colunas 100% empilhadas
            filtros 
                tipo de filtragem 
                    básica
                assunto
                    saúde 
            visualizações 
                criar visual 
                    grafico de colunas 100% empilhadas
                    eixo X 
                        Entrevistas[Entrevista abb] 
                    eixo Y 
                        Entrevistas[qtde_perguntas]
                    legenda 
                        Entrevistas[Resposta]
                    manter todos os filtros
                        habilitado 
                formatar visual 
                    visual 
                        eixo X 
                            valores 
                                habilitado 
                        eixo Y 
                            default 
                                insatisfeito [cor #EAA3D0]
                                neutro [cor #626AAB]
                                satisfeito[cor #5CF1E9]
                        legenda 
                            desabilitado 
                        rotulo de dados 
                            habilitado 
                                detalhes
                                    habilitado 
                    geral 
                        dicas de ferramenta 
                            habilitado 
        grafico de colunas 100% empilhadas
            filtros 
                tipo de filtragem 
                    básica
                assunto
                    carga horária 
            visualizações 
                criar visual 
                    grafico de colunas 100% empilhadas
                    eixo X 
                        Entrevistas[Entrevista abb] 
                    eixo Y 
                        Entrevistas[qtde_perguntas]
                    legenda 
                        Entrevistas[Resposta]
                    manter todos os filtros
                        habilitado 
                formatar visual 
                    visual 
                        eixo X 
                            valores 
                                habilitado 
                        eixo Y 
                            default 
                                insatisfeito [cor #EAA3D0]
                                neutro [cor #626AAB]
                                satisfeito[cor #5CF1E9]
                        legenda 
                            desabilitado 
                        rotulo de dados 
                            habilitado 
                                detalhes
                                    habilitado 
                    geral 
                        dicas de ferramenta 
                            habilitado 

        grafico de colunas 100% empilhadas
            filtros 
                tipo de filtragem 
                    básica
                assunto
                    salário 
            visualizações 
                criar visual 
                    grafico de colunas 100% empilhadas
                    eixo X 
                        Entrevistas[Entrevista abb] 
                    eixo Y 
                        Entrevistas[qtde_perguntas]
                    legenda 
                        Entrevistas[Resposta]
                    manter todos os filtros
                        habilitado 
                formatar visual 
                    visual 
                        eixo X 
                            valores 
                                habilitado 
                        eixo Y 
                            default 
                                insatisfeito [cor #EAA3D0]
                                neutro [cor #626AAB]
                                satisfeito[cor #5CF1E9]
                        legenda 
                            desabilitado 
                        rotulo de dados 
                            habilitado 
                                detalhes
                                    habilitado 
                    geral 
                        dicas de ferramenta 
                            habilitado 
            

### fonte de recrutamento 
    criar visual 
        treemap 
            categoria
                funcionario[Fonte Recrutamento]
            valores 
                Entrevistas[Qtde Funcionarios]
                    i.e., a nova medida Qtde Funcionarios da tabela Entrevistas (criada pela concatenação das planilhas 2019 e 2020)
        manter todos os filtros 
    formatar visual 
        visual 
            legenda 
                desabilidati 
            cores 
                atribuir 
            rotulos de dados 
                habilitados 
            rotulos de categorias 
                habilitados 
        geral 
            titulo 
                desabilitado 
            tela de fundo 
                desabilitado 
            icones de cabeçalho 
                habilitado 
            dicas de ferramenta 
                habilitado 

### range de idade [faixa etária] 
    power query 
        tabela funcionario 
            adicionar coluna 
                coluna de exemplos 
                    da seleção 
                        funcionario[Idade]
                            criar duas linhas de few shots da faixa etária que foi determinada para conseguir uma coluna de intervalos respectiva às faixas etárias correspondentes 
                                funcionario[Range Idade]
    visualizações 
        criar visual 
            gráfico funil 
            categoria 
                funcionario[Range Idade]
            valores 
                Entrevistas[Qtde Funcionarios]
                    i.e., a nova medida que foi criada 
            manter todos os filtros 
                habilitado 
        formatar visual 
            visual 
                cores 
                    atribuir ou default 
                        #FFFF00
                rotulos de dados 
                    habilitado 
                rotulos de categorias 
                    habilitado 
            geral 
                propriedades 
                    default 
                titulo 
                    desabilitado 
                tela de fundo 
                    desabilitado 
                icones de cabeçalho 
                    habilitado 
                dicas de ferramenta 
                    habilitado 

### qtde funcionarios por ano 
    visualizações
        criar visual
            grafico de colunas 
            eixo X 
                funcionario[Ano Contratacao]
                    date hierarchy 
                        year 
            eixo Y 
                Entrevistas[Qtde Funcionarios]
            manter todos os filtros 
                habilitado 
        formatar visual 
            visual 
                eixo X
                    valores 
                        habilitado 
                eixo Y
                    valores 
                        desabilitado 
                rotulos de dados
                    habilitado 
                        valor 
                            habilitado 
            geral 
                tela de fundo 
                    desabilitado 
                ícones de cabeçalho 
                    habilitado 


    
        


    
    