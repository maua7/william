<!DOCTYPE html>
<html lang="en">

    <head>
        <meta charset="UTF-8">
        <!-- <script data-require="mustache.js@0.7.2" data-semver="0.7.2" src="https://cdnjs.cloudflare.com/ajax/libs/mustache.js/0.7.2/mustache.js"></script> -->
        <!-- <script data-require="jquery@2.2.0" data-semver="2.2.0" src="https://ajax.googleapis.com/ajax/libs/jquery/2.2.0/jquery.min.js"></script> -->
        <script src="https://cdnjs.cloudflare.com/ajax/libs/numeral.js/2.0.6/numeral.min.js"></script>
        <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/css/bootstrap.min.css" integrity="sha384-Gn5384xqQ1aoWXA+058RXPxPg6fy4IWvTNh0E263XmFcJlSAwiGgFAW/dAiS6JXm"
            crossorigin="anonymous">
        <script src="https://code.jquery.com/jquery-3.2.1.slim.min.js" integrity="sha384-KJ3o2DKtIkvYIK3UENzmM7KCkRr/rE9/Qpg6aAZGJwFDMVNA/GpGFF93hXpG5KkN" crossorigin="anonymous"></script>
        <script src="https://cdn.jsdelivr.net/npm/popper.js@1.12.9/dist/umd/popper.min.js" integrity="sha384-ApNbgh9B+Y1QKtv3Rn7W3mgPxhU9K/ScQsAP7hUibX39j7fakFPskvXusvfa0b4Q" crossorigin="anonymous"></script>
        <script src="https://cdn.jsdelivr.net/npm/bootstrap@4.0.0/dist/js/bootstrap.min.js" integrity="sha384-JZR6Spejh4U02d8jOt6vLEHfe/JQGiRRSQQxSfFWpi1MquVdAyjUar5+76PVCmYl" crossorigin="anonymous"></script>
        <link href="https://fonts.googleapis.com/css?family=Roboto" rel="stylesheet">
        <script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>

        <style>
            html, body{ font-family: 'Roboto', sans-serif; font-size: 13px; background: transparent; }
            span.count{ font-size: 40px; line-height: 40px; }       
            .ranking span.count{ font-size: 20px; line-height: 20px; }
            
            .card-footer{ font-size: 25px; font-weight: bold }

            @media only screen and (max-width: 768px) {
                .col-sm-12{
                    font-size: 15px; line-height: 15px;
                }
            }

            /* body {
                margin: 0;
                padding:0;

            } */

            .carousel-control-prev-icon {
                background-image: url("data:image/svg+xml;charset=utf8,%3Csvg xmlns='http://www.w3.org/2000/svg' fill='%2300000' viewBox='0 0 8 8'%3E%3Cpath d='M5.25 0l-4 4 4 4 1.5-1.5-2.5-2.5 2.5-2.5-1.5-1.5z'/%3E%3C/svg%3E") !important;
            }

            .carousel-control-next-icon {
                background-image: url("data:image/svg+xml;charset=utf8,%3Csvg xmlns='http://www.w3.org/2000/svg' fill='%2300000' viewBox='0 0 8 8'%3E%3Cpath d='M2.75 0l-1.5 1.5 2.5 2.5-2.5 2.5 1.5 1.5 4-4-4-4z'/%3E%3C/svg%3E") !important;
            }

            .row{ 
                margin-right:0;
                margin-left:0;
            } 

            .tituloVendedor{
                color: red;
                text-align: center;
                margin: -11px;
                font-size: 24px;
            }

            .tituloMetas{
                color: red;
            }

            span.count{
                font-size: 25px;
            }

            .teste{
                background-color: #5F9BD7;
            }

            .tituloFamilia{
                background-color: #0975E1;
                color: white;
                text-align: center;
                font-size: 19px;
            }

            .tituloPedidos{
                color: white;
            }

            .sizeVendas{
                font-size: 17px;
            }

            .testeDivTitulo {
                margin: -3px;
            }

            /* .card-body { */
                /* margin: -24px; */
                /* padding: 2px; */
                /* border: 2px solid red; */
            /* } */

            .testeBody {
                margin: -24px;
            }

            .titulosValores {
                font-size: 17px;
            }

            .editValorTotal {
                margin-left: 16px;
            }

            .mensalPadd {
                margin: 25px;
            }

            .diarioPadd {
                margin: 10px;
            }

            .boxDiario {
                border: 2px solid red;
            }

            .tituloTable {
                text-align: center;
                /* justify-content:right ; */
            }

            /* .tabela {
                position:absolute;
                top:50%;
                left:50%;
                margin-top:-100px;
                margin-left:-180px;
                font-weight:700;
            } */

            /* .testeCard {
                border: 2px solid red;
                margin-bottom: -50px;
                margin-top: -10px;
            } */

        </style>
    </head>

    <body>
        <div id="app">
            <div id="carouselExampleControls" class="carousel slide" data-ride="carousel">
                <div class="carousel-inner">
                    <div class="carousel-item" v-for="(item,index) in dataSlides" :class="{ active: index==0 }" >
                        <div class="d-block w-100" style="height: 100vh; width: 100vw;" alt="First slide">

                            <div v-if="index != dataSlides.length -1">
                                <div class="row">
                                    <div class="col-sm-12">
                                        <div class="clearfix">                                                                        
                                            <div class="float-right">
                                                <small>
                                                    <i>Atualizado em {{ item.DATA_ATUALIZACAO_MAQUINAS }}</i>
                                                </small>
                                            </div>
                                        </div>
                                    </div>
                                </div>     
                                
                                <div class="mb-0 testeDivTitulo">
                                    <h3 class="mb-0 tituloVendedor">{{ item.VENDEDOR_NOME }}</h3>
                                </div>
    
                                <div class="row mt-3" v-if="item.FAMILIA_DESCRICAO_MAQUINAS != ''">
                                    <div class="col-sm-12">
                                        <div class="card">
                                            <h3 class="mb-0 tituloFamilia">META FAMÍLIA {{ item.FAMILIA_DESCRICAO_MAQUINAS }}</h3>
                                            <div class="card-body">
                                                <div class="card-group">
                    
                                                    <div class="card">
                                                    <div class="card-body">
                                                        <div class="mt-3">
                                                            <div class="row mb-3">
                                                                <div class="col-sm-6">
                                                                    <div class="text-muted">VALOR</div>                        
                                                                    <span class="count">{{ item.VALOR_MENSAL_FORMATTED_MAQUINAS }}</span>     
                                                                </div>
                                                                <div class="col-sm-6">
                                                                    <div class="tituloMetas">META MENSAL</div>                        
                                                                    <span class="count">{{ item.METAMENSAL_FORMATTED_MAQUINAS }} </span>     
                                                                </div>
                                                            </div>                        
                                                            <div class="clearfix">                                                                        
                                                                <div class="float-right">
                                                                    <strong>{{ item.PERC_META_MENSAL }}%</strong>
                                                                </div>
                                                            </div>
                                                            <div class="progress">
                                                                <div class="progress-bar" :class="[item.progress2_class_MAQUINAS]" role="progressbar" :style="{ 'width': item.PERC_META_MENSAL_MAQUINAS  + '%' }" aria-valuenow="{{ item.PERC_META_MENSAL_MAQUINAS }}" aria-valuemin="0" aria-valuemax="100"></div>
                                                            </div>
                                                        </div>
                                                    </div>
                                                    </div>
                                                    
                                                    <div class="card teste col-xs-12 col-sm-3 col-md-3 col-lg-3 pr-1">
                                                        <div class="card-body testeCard px-1">
                                                        <h5 class="tituloPedidos px-3 pt-1">Pedidos de vendas</h5>
                                                        <div class="mt-3 px-1">
                                                            <div class="row mb-3 px-0 pt-3">
                                                                <div class="col-sm-4 px-1">
                                                                    <span class="count">Qtd: {{ item.QTDE_PARADO_MAQUINAS }}</span>     
                                                                </div>
                                                                <div class="col-sm px-0 d-flex justify-content-end">
                                                                    <span class="count">{{ item.NOVO_VALOR_PARADO_MAQUINAS }}</span>
                                                                </div>
                                                            </div>                        
                                                        </div>
                                                        </div>
                                                    </div>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </div> 

                                
                                <div class="row mt-3">
                                    <div class="col-sm-12" v-if="item.FAMILIA_DESCRICAO_PECAS != ''">
                                        <div class="card">
                                            <h3 class="mb-0 tituloFamilia">META FAMÍLIA {{ item.FAMILIA_DESCRICAO_PECAS }}</h3>
                                            <div class="card-body">
                                                <!--TESTE NET AQUI   -->
                                                <div class="card-group">
                        
                                                    <div class="card">
                                                    <div class="card-body">
                                                        <!-- <b class="titulosValores">MENSAL</b>  -->
                                                        <div class="mt-3">
                                                            <div class="row mb-3">
                                                                <div class="col-sm-6">
                                                                    <div class="text-muted">VALOR</div>                        
                                                                    <span class="count">{{ item.VALOR_MENSAL_FORMATTED_PECAS }}</span>     
                                                                </div>
                                                                <div class="col-sm-6">
                                                                    <div class="tituloMetas">META MENSAL</div>                        
                                                                    <span class="count">{{ item.METAMENSAL_FORMATTED_PECAS }} </span>     
                                                                </div>
                                                            </div>                        
                                                            <div class="clearfix">                                                                        
                                                                <div class="float-right">
                                                                    <strong>{{ item.PERC_META_MENSAL_PECAS }}%</strong>
                                                                </div>
                                                            </div>
                                                            <div class="progress">
                                                                <div class="progress-bar" :class="[item.progress2_class_PECAS]" role="progressbar" :style="{ 'width': item.PERC_META_MENSAL_PECAS  + '%' }" aria-valuenow="{{ item.PERC_META_MENSAL_PECAS }}" aria-valuemin="0" aria-valuemax="100"></div>
                                                            </div>
                                                        </div>
                                                    </div>
                                                    </div>
                                                    
                                                    <div class="card teste col-xs-12 col-sm-3 col-md-3 col-lg-3 pr-1">
                                                        <div class="card-body testeCard px-1">
                                                        <!-- <b>PEDIDOS DE VENDAS</b>  -->
                                                        <h5 class="tituloPedidos px-3 pt-1">Pedidos de vendas</h5>
                                                        <div class="mt-3 px-1">
                                                            <div class="row mb-3 px-0 pt-3">
                                                                <div class="col-sm-4 px-1">
                                                                    <span class="count">Qtd: {{ item.QTDE_PARADO_PECAS }}</span>     
                                                                </div>
                                                                <div class="col-sm px-0 d-flex justify-content-end">
                                                                    <span class="count">{{ item.NOVO_VALOR_PARADO_PECAS }}</span>
                                                                </div>
                                                            </div>                        
                                                        </div>
                                                        </div>
                                                    </div>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                    
                                    
                        
                                    <div class="col-sm-12">
                                        <div class="card">
                                            <h3 class="mb-0 tituloFamilia">META GERAL VENDEDOR </h3>
                                            <div class="card-body">
                                                <div class="card-group">
                                                <div class="card">
                                                    <div class="card-body">
                                                        <div class="mt-3">
                                                            <div class="row mb-3">
                                                                <div class="col-sm-6">
                                                                    <div class="text-muted">VALOR</div>                        
                                                                    <span class="count">{{ item.VALOR_MENSAL_SOMADO }}</span>     
                                                                </div>
                                                                <div class="col-sm-6">
                                                                    <div class="tituloMetas">META MENSAL</div>                        
                                                                    <span class="count">{{ item.META_MENSAL_SOMADA }} </span>     
                                                                </div>
                                                            </div>                        
                                                            <div class="clearfix">                                                                        
                                                                <div class="float-right">
                                                                    <strong>{{ item.PERC_META_MENSAL }}%</strong>
                                                                </div>
                                                            </div>
                                                            <div class="progress">
                                                                <div class="progress-bar" :class="[item.progress2_class]" role="progressbar" :style="{ 'width': item.PERC_META_MENSAL  + '%' }" aria-valuenow="{{ item.PERC_META_MENSAL }}" aria-valuemin="0" aria-valuemax="100"></div>
                                                            </div>
                                                        </div>
                                                    </div>
                                                    </div>
                                                    
                                                    <div class="card d-flex teste col-xs-12 col-sm-3 col-md-3 col-lg-3 pr-1">
                                                        <div class="card-body testeCard px-1">
                                                        <h5 class="tituloPedidos px-3 pt-1">Pedidos de vendas</h5>
                                                        <div class="mt-3 px-1">
                                                            <div class="row mb-3 px-0 pt-3">
                                                                <div class="col-sm-4 px-1">
                                                                    <span class="count">Qtd: {{ item.QTD_SOMADO }}</span>     
                                                                </div>
                                                                <div class="col-sm px-0 d-flex justify-content-end">
                                                                    <span class="count">{{ item.VALO_QTD_SOMADO }}</span>     
                                                                </div>
                                                            </div>                        
                                                        </div>
                                                        </div>
                                                    </div>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
    
                                </div>

                                
                            </div>
                            
                            <!-- tabela -->
                            <div style="padding-top: 3rem;" v-if="index == dataSlides.length -1">
                                <div class="row" >
                                    <div  class="col-12" style="width: 100vw;">
                                        <div class=" ranking">
                                            <div class="header">
                                                <h3 class="mb-0 tituloTable">GERAL</h3>
                                            </div>
                                            <table class="table table-striped tabela">
                                                <thead>
                                                <tr>
                                                    <th scope="col">Vendedor</th>
                                                    <th scope="col">Meta</th>
                                                    <th scope="col">Venda de maquinas</th>
                                                    <th scope="col">Venda de peças</th>
                                                </tr>
                                                </thead>
                                                <tbody v-for="itemTabela in tabelaGeral">
                                                    <tr>
                                                        <td> {{ itemTabela.VENDEDOR_NOME  }} </td>
                                                        <td> {{ itemTabela.META_MENSAL_SOMADA }} </td>
                                                        <td> {{ itemTabela.VALOR_MENSAL_MAQUINAS }} </td>
                                                        <td> {{ itemTabela .VALOR_MENSAL_PECAS  }} </td>
                                                    </tr>                                    
                                                </tbody>
                                            </table>
                                        </div>
                                    </div>
                                </div>
                            </div>
                            
                            <!-- fim da tabela -->

                            <!--teste 2-->

                        </div>
                    </div>
                </div>        

                <a  class="carousel-control-prev" href="#carouselExampleControls" role="button" data-slide="prev">
                  <span class="carousel-control-prev-icon" aria-hidden="true"></span>
                  <!-- <button type="button" class="btn btn-primary">Previous</button>  -->
                  <!-- <button class="sr-only">Previous</button> -->
                </a>

                <a class="carousel-control-next" href="#carouselExampleControls" role="button" data-slide="next">
                  <span class="carousel-control-next-icon" aria-hidden="true"></span>
                  <!-- <button type="button" class="btn btn-primary">next</button>  -->
                  <!-- <button class="sr-only">Next</button> -->
                </a>
            </div>
        </div>
        <script src="https://code.jquery.com/jquery-3.3.1.min.js"
        integrity="sha256-FgpCb/KJQlLNfOu91ta32o/NMZxltwRo8QtmkMRdAu8=" crossorigin="anonymous"></script>

        <script>
            // let resultado = [{"VENDEDOR_NOME":"ALMEIDA","ANO":"2023","PERC_META_DIARIA":30.0101,"DATA_ATUALIZACAO":"2023-06-21 14:25:01","QTDE_PARADO":11,"UTEIS":22,"QTDE_VENDAS":55,"VALOR_MEDIA":2785.74,"FAMILIA_DESCRICAO":"MAQUINAS","VALOR_MENSAL":153215.95,"MEDIA_POR_VENDEDOR":153215.95,"MES":"06","NUMERO_VENDEDORES":1,"METAMENSAL":450000,"METADIARIA":20454.55,"VALOR_DIARIO":6138.44,"VALOR_PARADO":29035.13,"PERC_META_MENSAL":34.04},{"VENDEDOR_NOME":"ALMEIDA","ANO":"2023","PERC_META_DIARIA":0,"DATA_ATUALIZACAO":"2023-06-21 14:25:01","QTDE_PARADO":0,"UTEIS":22,"QTDE_VENDAS":0,"VALOR_MEDIA":0,"FAMILIA_DESCRICAO":"PEÇAS","VALOR_MENSAL":0,"MEDIA_POR_VENDEDOR":0,"MES":"06","NUMERO_VENDEDORES":1,"METAMENSAL":1,"METADIARIA":0.05,"VALOR_DIARIO":0,"VALOR_PARADO":0,"PERC_META_MENSAL":0},{"VENDEDOR_NOME":"ANA ","ANO":"2023","PERC_META_DIARIA":34.6208,"DATA_ATUALIZACAO":"2023-06-21 14:25:01","QTDE_PARADO":6,"UTEIS":22,"QTDE_VENDAS":29,"VALOR_MEDIA":7677.15,"FAMILIA_DESCRICAO":"MAQUINAS","VALOR_MENSAL":222637.39,"MEDIA_POR_VENDEDOR":222637.39,"MES":"06","NUMERO_VENDEDORES":1,"METAMENSAL":550000,"METADIARIA":25000,"VALOR_DIARIO":8655.2,"VALOR_PARADO":48949.02,"PERC_META_MENSAL":40.47},{"VENDEDOR_NOME":"ANA ","ANO":"2023","PERC_META_DIARIA":24.1381,"DATA_ATUALIZACAO":"2023-06-21 14:25:01","QTDE_PARADO":10,"UTEIS":22,"QTDE_VENDAS":23,"VALOR_MEDIA":4452.76,"FAMILIA_DESCRICAO":"PEÇAS","VALOR_MENSAL":102413.5,"MEDIA_POR_VENDEDOR":102413.5,"MES":"06","NUMERO_VENDEDORES":1,"METAMENSAL":200000,"METADIARIA":9090.91,"VALOR_DIARIO":2194.38,"VALOR_PARADO":15774.79,"PERC_META_MENSAL":51.2},{"VENDEDOR_NOME":"CARLA","ANO":"2023","PERC_META_DIARIA":58.298,"DATA_ATUALIZACAO":"2023-06-21 14:25:01","QTDE_PARADO":16,"UTEIS":22,"QTDE_VENDAS":54,"VALOR_MEDIA":2442.56,"FAMILIA_DESCRICAO":"MAQUINAS","VALOR_MENSAL":131898.11,"MEDIA_POR_VENDEDOR":131898.11,"MES":"06","NUMERO_VENDEDORES":1,"METAMENSAL":320000,"METADIARIA":14545.45,"VALOR_DIARIO":8479.72,"VALOR_PARADO":41749.51,"PERC_META_MENSAL":41.21}]
            // let resultado = $.ajax({
            //     type: 'GET',
            //     url: "consult.json",
            //     async: false,
            //     dataType: 'json',
            //     complete: function (result) {
            //         return result;
            //     }
            // }).responseText;

            // resultado = JSON.parse(resultado);

            numeral.register('locale', 'brasil', {
                delimiters: {
                    thousands: '.',
                    decimal: ','
                },
                currency: {
                    symbol: 'R$ '
                }
            });

            numeral.locale('brasil');
            numeral.defaultFormat('$ 0,0.00');

            const myApp = {
                data() {
                    return {
                        vendedores : [],
                        ranking : [],
                        arrayCalculoGeral : [],
                        novosVendedores : [],
                        metasCalculadas : [],
                        dataSlides : [],
                        data : [],
                        resultadoAgrupado : [],
                        tabelaGeral : []
                    }
                },
                mounted() {
                    debugger
                    this.ranking = resultado.slice()
                    this.addGeral();
                    this.ordenaVendedores();
                    this.createBarProgress();
                    this.renderTemplate();
                    this.createData();
                },
                methods: {
                    addGeral() {
                        debugger
                        this.ranking = this.ranking.sort(function (a, b) {
                            if (a.VALOR_MENSAL > b.VALOR_MENSAL)
                                return -1
                            if (a.VALOR_MENSAL < b.VALOR_MENSAL)
                                return 1;
                            return 0;
                        })

                    },

                    ordenaVendedores() {
                        for (var i = 0; i < this.ranking.length; i++) {
                            var row = this.ranking[i];
                            if (row.VENDEDOR_NOME == "GERAL") {                
                                geral = row;
                                this.ranking.splice(i, 1);
                            }
                        }
                    },

                    createBarProgress() {
                        for (var i = 0; i < resultado.length; i++) {
                            var row = resultado[i];
                            var date = new Date(row.DATA_ATUALIZACAO);
                            row.DATA_ATUALIZACAO = ('0' + date.getDate()).slice(-2) + '/' 
                                + ('0' + (date.getMonth() + 1)).slice(-2) + '/' + date.getFullYear() + ' ás ' 
                                    + ('0' + date.getHours()).slice(-2) + ':' + ('0' + date.getMinutes()).slice(-2);

                            if (row.VENDEDOR_NOME == 'GERAL') {
                                geral = row;
                            }

                            row.progress1_class = 'bg-success';
                            if (row.PERC_META_DIARIA <= 70) {
                                row.progress1_class = 'bg-warning';
                            }

                            if (row.PERC_META_DIARIA <= 50) {
                                row.progress1_class = 'bg-danger';
                            }

                            row.progress2_class = 'bg-success';
                            if (row.PERC_META_MENSAL <= 70) {
                                row.progress2_class = 'bg-warning';
                            }

                            if (row.PERC_META_MENSAL <= 50) {
                                row.progress2_class = 'bg-danger';
                            }

                            this.vendedores.push(row);
                        }
                    },

                    agruparPorFamilia() {
                        vendedores.forEach(element => {
                            if (element.VENDEDOR_NOME != "GERAL") {
                                let somaMetas = 0;
                                let objeto = result[element.VENDEDOR_NOME];

                                if (objeto) {
            
                                    objeto.META =  element.METAMENSAL;
                                    if (element.FAMILIA_DESCRICAO == "MAQUINAS") {
                                        objeto.VENDA_MAQUINA = numeral(element.VALOR_MENSAL).format();
                                    } else if (element.FAMILIA_DESCRICAO == "PEÇAS") {
                                        objeto.VENDA_PECAS = numeral(element.VALOR_MENSAL).format()
                                    }

                                    result[element.VENDEDOR_NOME] = objeto;
                                
                                } else {
                                    
                                    result[element.VENDEDOR_NOME] = {
                                        VENDEDOR: element.VENDEDOR_NOME,
                                        META: element.METAMENSAL,
                                        VENDA_MAQUINA: numeral(element.VALOR_MENSAL).format(),
                                        VENDA_PECAS: numeral(element.VALOR_MENSAL).format()
                                    }
                                }
                            }
                            
                        });
                    },

                    calculaVendedoresAtivos() {
                        let calcValorDiario = 0;
                        let calcMetaDiaria = 0;
                        let calcMetaMensal = 0;
                        let calcValorMensal = 0;
                        let calcQtdParado = 0;
                        let calcValorQtdParado = 0;
                        let calcPercMensal = 0;
                        let calcPercDiario = 0;

                        let objetoCalculoGeral = {};
                        this.data.forEach(element => {
                            calcValorDiario = this.somaArredondada(element.VALOR_DIARIO_PECAS, element.VALOR_DIARIO_MAQUINAS);
                            calcMetaMensal = this.somaArredondada(element.METAMENSAL_PECAS, element.METAMENSAL_MAQUINAS);
                            calcMetaDiaria = this.somaArredondada(element.METADIARIA_MAQUINAS, element.METADIARIA_PECAS);
                            calcValorMensal = this.somaArredondada(element.VALOR_MENSAL_MAQUINAS, element.VALOR_MENSAL_PECAS);
                            calcPercDiario = (calcValorDiario/calcMetaDiaria)*100; 
                            calcPercMensal = (calcValorMensal/calcMetaMensal)*100;
                            
                            calcQtdParado = this.somaArredondada(element.QTDE_PARADO_MAQUINAS, element.QTDE_PARADO_PECAS);
                            calcValorQtdParado = this.somaArredondada(element.VALOR_PARADO_PECAS, element.VALOR_PARADO_MAQUINAS);
                            objetoCalculoGeral = {
                                VENDEDOR_NOME : element.VENDEDOR_NOME,
                                VALOR_MENSAL_MAQUINAS : element.VALOR_MENSAL_MAQUINAS,
                                VALOR_MENSAL_PECAS : element.VALOR_MENSAL_PECAS,
                                META_DIARIA_SOMADA : numeral(calcMetaDiaria).format(),
                                VALOR_DIARIO_SOMADO : numeral(calcValorDiario).format(),
                                META_MENSAL_SOMADA : numeral(calcMetaMensal).format(),
                                VALOR_MENSAL_SOMADO : numeral(calcValorMensal).format(),
                                QTD_SOMADO : calcQtdParado,
                                VALO_QTD_SOMADO : numeral(calcValorQtdParado).format(),
                                PERC_META_MENSAL : calcPercMensal.toFixed(2),
                                PERC_META_DIARIA : calcPercDiario.toFixed(2),
                            }

                            this.arrayCalculoGeral.push(objetoCalculoGeral);
                        });
                    },

                    somaArredondada(v1, v2) {
                        let v1Arredondado = parseFloat(parseFloat(v1).toFixed(2)) * 100;
                        let v2Arredondado = parseFloat(parseFloat(v2).toFixed(2)) * 100;
                        let resultadoSoma = v1Arredondado + v2Arredondado;
                        resultadoSoma /= 100;
                        return resultadoSoma;
                    },

                    formatMoney(params) {
                        if (params.value) {
                            return accounting.formatMoney(params.value, 'R$ ', 2, '.', ',');
                        }
                        return null;
                    },

                    renderTemplate() {
                        debugger
                        this.vendedores.forEach(function(row){                
                            if(typeof row.MEDIA_POR_VENDEDOR == 'number')
                                row.MEDIA_POR_VENDEDOR_FORMATTED = numeral(row.MEDIA_POR_VENDEDOR).format();
                            
                            if(typeof row.VALOR_MEDIA == 'number')
                                row.VALOR_MEDIA_FORMATTED = numeral(row.VALOR_MEDIA).format();
                            
                            if(typeof row.VALOR_MENSAL == 'number')
                                row.VALOR_MENSAL_FORMATTED = numeral(row.VALOR_MENSAL).format();
                            
                            if(typeof row.METAMENSAL == 'number')
                                row.METAMENSAL_FORMATTED = numeral(row.METAMENSAL).format();
                            
                            if(typeof row.METADIARIA == 'number')
                                row.METADIARIA_FORMATTED = numeral(row.METADIARIA).format();
                            
                            //if(typeof row.VALOR_DIARIO == 'number')
                                row.VALOR_DIARIO_FORMATTED = numeral(parseFloat(row.VALOR_DIARIO)).format();
                        })
                    },

                    createData() {
                        debugger
                        let vendedor = {
                            VENDEDOR_NOME : '',
                            FAMILIA_DESCRICAO_MAQUINAS : '',
                            FAMILIA_DESCRICAO_PECAS : '',
                            FAMILIA_DESCRICAO_PECAS: 0,
                            VALOR_MEDIA_FORMATTED_PECAS: 0,
                            PERC_META_MENSAL_PECAS: 0,
                            METAMENSAL_FORMATTED_PECAS: 0,  
                            QTDE_PARADO_PECAS: 0,
                            NOVO_VALOR_PARADO_PECAS: 0,
                            VALOR_MENSAL_FORMATTED_PECAS: 0,
                            VALOR_DIARIO_PECAS: 0,
                            METAMENSAL_PECAS: 0,
                            METADIARIA_PECAS: 0,
                            VALOR_MENSAL_PECAS: 0, 
                            QTDE_PARADO_PECAS : 0,
                            VALOR_PARADO_PECAS: 0,
                            VALOR_MENSAL_SOMADO: 0,
                            FAMILIA_DESCRICAO_MAQUINAS: 0,
                            VALOR_MEDIA_FORMATTED_MAQUINAS : 0,
                            VALOR_MENSAL_FORMATTED_MAQUINAS :0,
                            progress2_class_MAQUINAS : 0,
                            PERC_META_MENSAL_MAQUINAS : 0,
                            METAMENSAL_FORMATTED_MAQUINAS : 0,
                            DATA_ATUALIZACAO_MAQUINAS : 0,
                            QTDE_PARADO_MAQUINAS : 0,
                            VALOR_DIARIO_MAQUINAS : 0,
                            METAMENSAL_MAQUINAS : 0,
                            METADIARIA_MAQUINAS : 0,
                            VALOR_MENSAL_MAQUINAS : 0,
                            VALOR_PARADO_MAQUINAS : 0,
                            NOVO_VALOR_PARADO_MAQUINAS: 0,
                        }

                        let auxFamilia = this.vendedores[0].FAMILIA_DESCRICAO;
                        let auxVendedor = this.vendedores[0].VENDEDOR_NOME;
                        console.log(this.vendedores);
                        for (let i = 0; i < this.vendedores.length; i++) {
                            const element = this.vendedores[i];
                            
                            
                            if (element.FAMILIA_DESCRICAO == "MAQUINAS") {
                                vendedor.FAMILIA_DESCRICAO_MAQUINAS = element.FAMILIA_DESCRICAO;
                                vendedor.VALOR_MEDIA_FORMATTED_MAQUINAS = element.VALOR_MEDIA_FORMATTED;
                                vendedor.VALOR_MENSAL_FORMATTED_MAQUINAS = element.VALOR_MENSAL_FORMATTED;
                                vendedor.progress2_class_MAQUINAS =element.progress2_class;
                                vendedor.PERC_META_MENSAL_MAQUINAS =element.PERC_META_MENSAL;
                                vendedor.METAMENSAL_FORMATTED_MAQUINAS =element.METAMENSAL_FORMATTED;
                                vendedor.DATA_ATUALIZACAO_MAQUINAS = element.DATA_ATUALIZACAO;
                                vendedor.QTDE_PARADO_MAQUINAS = element.QTDE_PARADO;
                                vendedor.VALOR_DIARIO_MAQUINAS = element.VALOR_DIARIO;
                                vendedor.METAMENSAL_MAQUINAS = element.METAMENSAL;
                                vendedor.METADIARIA_MAQUINAS = element.METADIARIA;
                                vendedor.VALOR_MENSAL_MAQUINAS = element.VALOR_MENSAL;
                                vendedor.VALOR_PARADO_MAQUINAS = element.VALOR_PARADO;
                                vendedor.NOVO_VALOR_PARADO_MAQUINAS = numeral(element.VALOR_PARADO).format();
                            } 

                            vendedor.VENDEDOR_NOME = element.VENDEDOR_NOME;

                            if (element.FAMILIA_DESCRICAO == "PEÇAS") {
                                vendedor.FAMILIA_DESCRICAO_PECAS = element.FAMILIA_DESCRICAO;
                                vendedor.VALOR_MEDIA_FORMATTED_PECAS = element.VALOR_MEDIA_FORMATTED;
                                vendedor.progress2_class_PECAS = element.progress2_class;
                                vendedor.PERC_META_MENSAL_PECAS = element.PERC_META_MENSAL;
                                vendedor.METAMENSAL_FORMATTED_PECAS = element.METAMENSAL_FORMATTED;
                                vendedor.QTDE_PARADO_PECAS = element.QTDE_PARADO;
                                vendedor.NOVO_VALOR_PARADO_PECAS = numeral(element.VALOR_PARADO).format();
                                vendedor.VALOR_MENSAL_FORMATTED_PECAS = element.VALOR_MENSAL_FORMATTED;
                                vendedor.VALOR_DIARIO_PECAS = element.VALOR_DIARIO;
                                vendedor.METAMENSAL_PECAS = element.METAMENSAL;
                                vendedor.METADIARIA_PECAS = element.METADIARIA;
                                vendedor.VALOR_MENSAL_PECAS = element.VALOR_MENSAL;
                                vendedor.QTDE_PARADO_PECAS = element.QTDE_PARADO;
                                vendedor.VALOR_PARADO_PECAS = element.VALOR_PARADO;
                                vendedor.VALOR_MENSAL_SOMADO = element.VALOR_MENSAL_SOMAD0;
                            }

                            console.log(this.vendedores);

                            if (this.vendedores.length > i+1) {
                                auxVendedor = this.vendedores[i+1].VENDEDOR_NOME;
                            }

                            if (element.VENDEDOR_NOME != auxVendedor || auxVendedor == '') {
                                this.data.push(vendedor)
                                vendedor = {
                                    VENDEDOR_NOME : '',
                                    FAMILIA_DESCRICAO_MAQUINAS : '',
                                    FAMILIA_DESCRICAO_PECAS : '',
                                    FAMILIA_DESCRICAO_PECAS: 0,
                                    VALOR_MEDIA_FORMATTED_PECAS: 0,
                                    PERC_META_MENSAL_PECAS: 0,
                                    METAMENSAL_FORMATTED_PECAS: 0,  
                                    QTDE_PARADO_PECAS: 0,
                                    NOVO_VALOR_PARADO_PECAS: 0,
                                    VALOR_MENSAL_FORMATTED_PECAS: 0,
                                    VALOR_DIARIO_PECAS: 0,
                                    METAMENSAL_PECAS: 0,
                                    METADIARIA_PECAS: 0,
                                    VALOR_MENSAL_PECAS: 0, 
                                    QTDE_PARADO_PECAS : 0,
                                    VALOR_PARADO_PECAS: 0,
                                    VALOR_MENSAL_SOMADO: 0,
                                    FAMILIA_DESCRICAO_MAQUINAS: 0,
                                    VALOR_MEDIA_FORMATTED_MAQUINAS : 0,
                                    VALOR_MENSAL_FORMATTED_MAQUINAS :0,
                                    progress2_class_MAQUINAS : 0,
                                    PERC_META_MENSAL_MAQUINAS : 0,
                                    METAMENSAL_FORMATTED_MAQUINAS : 0,
                                    DATA_ATUALIZACAO_MAQUINAS : 0,
                                    QTDE_PARADO_MAQUINAS : 0,
                                    VALOR_DIARIO_MAQUINAS : 0,
                                    METAMENSAL_MAQUINAS : 0,
                                    METADIARIA_MAQUINAS : 0,
                                    VALOR_MENSAL_MAQUINAS : 0,
                                    VALOR_PARADO_MAQUINAS : 0,
                                    NOVO_VALOR_PARADO_MAQUINAS: 0,
                                }
                                auxVendedor = ''
                            }
                        }
                        console.log(this.data);
                        this.calculaVendedoresAtivos();
                        for (let i = 0; i < this.data.length; i++) {
                            this.dataSlides.push(Object.assign(this.data[i],this.arrayCalculoGeral[i]))          
                        }
                        
                        this.dataSlides.push({tabela : this.arrayCalculoGeral});

                        this.tabelaGeral = this.dataSlides[this.dataSlides.length -1].tabela;
                        
                    }
                }
            }           

            Vue.createApp(myApp).mount('#app');
        </script>
    </body>
</html>
