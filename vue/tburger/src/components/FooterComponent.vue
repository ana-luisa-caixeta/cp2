<template>
    <div>
        <footer id="footer">
            <p>Construído por Ana Luísa Caixeta &copy; 2024</p>
        </footer>
    </div>
</template>

<script>
    export default{
        name: "FooterComponent",
    }
</script>

<style scoped>
    #footer {
        height: 80px;
        background-color: #222;
        color: orangered;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    #footer p {
        font-size: 14px;
    }
</style>