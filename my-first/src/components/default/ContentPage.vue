<template>
    <section>
        <div>
            <p>Meu Conteudo</p>
            <div>
                <input placeholder="Digite seu nome" v-model="nome">
                <p>Seu nome é: {{ nome }}</p>
                <button @click="submeterFormulario()">Verificar Nome</button>

                <p v-if="url">
                    {{ url }}
                </p>
            </div>
        </div>
    </section>

</template>

<script>


    export default {
        name: "ContentPage",
        data() {
            return {
                nome:'',
                url: ''
            }
        },
        methods: {
            submeterFormulario(){
                let response = fetch('https://api.github.com/users/${this.nome}').then((data) => {
                    this.url = data.url;
                    console.log(data.url);
                });
            }
        }
    }
</script>

<style>

</style>