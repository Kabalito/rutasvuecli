<template>
    <v-container>
        <v-layout justify-center>
            <v-flex xs12 sm8 md6>
                <v-card>
                    <v-toolbar color="green" dark flat>
                        <v-toolbar-title>LISTA DE USUARIOS</v-toolbar-title>
                    </v-toolbar>
                    <v-list>
                        <v-list-tile :to="`/usuarios/${usuario.id}`" v-for="usuario in usuarios" :key="usuario.id">
                            {{usuario.name}}
                        </v-list-tile>
                    </v-list>
                </v-card>
            </v-flex>
        </v-layout>
    </v-container>
</template>

<script>
import axios from 'axios'
export default {
    data(){
        return {
            usuarios:[]
        }
    },
    beforeMount(){
        axios.get('https://jsonplaceholder.typicode.com/users').then((response)=>{
            this.usuarios = response.data
        }).catch((error)=>{
            console.log(error)
        })
    }
}
</script>

<style>

</style>