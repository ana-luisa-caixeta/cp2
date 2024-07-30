<template>
    <div id="pedidos-tabela">
        <!-- Adicione o componente de mensagem para exibir alertas de erro e sucesso -->
        <div>
            <div id="pedidos-tabela-cabecalho">
                <div id="ordem-id">#ID</div>
                <div>Nome</div>
                <div>Hamburger</div>
                <div>Ponto</div>
                <div>Opcionais</div>
                <div>Status</div>
                <div id="div-acoes">Ações</div>
            </div>
        </div>

        <!-- Quando não tiver nenhum pedido, somente o componente de mensagem é para ser apresentado -->
        <div class="pedidos-tabela-linha" v-for="pedido in listaPedidosRealizado" :key="pedido.id">
            <div id="ordem-numero">{{ pedido.id }}</div>

            <div id="ordem-numero">{{ pedido.nome }}</div>

            <div id="ordem-numero">{{ pedido.hamburguer.nome }}</div>

            <div id="ordem-numero">{{ pedido.ponto.descricao }}</div>

            <div>
                <ul>
                    <li v-for="(complemento, index) in pedido.complementos" :key="index">{{ complemento.nome }}</li>
                </ul>
            </div>

            <div class="divisor"></div>

            <ul>
                <li v-for="bebida in pedido.bebidas" :key="bebida.id">{{ bebida.nome }}</li>
            </ul>

            <div>
                <select name="status" id="status">
                    <option value="">Selecione</option>
                    <option v-for="status in listaStatusPedido" :key="status.id" :value="status.id" :selected="status.id == pedido.statusId">{{ status.descricao }}</option>
                </select>
            </div>
            
            <div id="div-acoes">
                <img src="./img/icone_lixeira.png" alt="Excluir" width="35px" height="35px">
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "ListaPedidoComponent",
        data() {
            return {
                listaPedidosRealizado: [],
                listaStatusPedido: []
            }
        },
        methods: {
            // Consultar pedidos
            async consultarPedidos() {
                const response = await fetch("https://tburger.wiremock.cloud/pedidos");
                this.listaPedidosRealizado = await response.json();
            },

            // Consultar status
            async consultarStatus() {
                const response = await fetch("https://tburger.wiremock.cloud/status_pedido");
                this.listaStatusPedido = await response.json();
            },

            // Deletar o pedido

            // Atualizar o pedido
        },
        mounted() {
            this.consultarPedidos();
            this.consultarStatus();
        }
    }
</script>

<style scoped>

</style>