<template>
    <div>
        <h1>Configurar Pedido</h1>
        <PedidoComponent :burguer="hamburguerSelecionado ? hamburguerSelecionado : {}"/>
    </div>
</template>

<script>
    import PedidoComponent from '../components/PedidoComponent.vue';

    export default {
        name: "ConfiguracaoPedidoView",
        data() {
            return {
                hamburguerSelecionado : null,
            };
        },
        components: { PedidoComponent },
        mounted() {
        console.log(this.$route.query);
        const burguerDecode = decodeURIComponent(this.$route.query.burguer);
        const burguerJson = JSON.parse(burguerDecode);
        this.hamburguerSelecionado = burguerJson;
        }
    }
</script>

<style scoped>

</style>