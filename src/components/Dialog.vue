<template>
    <v-row justify="center">
        <v-dialog v-model="dialog" persistent max-width="290">
            <template v-slot:activator="{ on, attrs }">
                <v-btn class="c" v-bind="attrs" v-on="on">
                    удалить
                </v-btn>
            </template>
            <v-card>
                <v-card-title class="text-h5">
                    Вы хотите удалить этот элемент?
                </v-card-title>
                <v-card-actions>
                    <v-spacer></v-spacer>
                    <v-btn color="green darken-1" text @click="dialog = false">
                        Не соглашаться
                    </v-btn>
                    <v-btn color="green darken-1" text @click="
                    dialog = false; agree()">
                        Соглашаться
                    </v-btn>
                </v-card-actions>
            </v-card>
        </v-dialog>
    </v-row>
</template>
<script>
import axios from 'axios';

export default {
    data() {
        return {
            dialog: false,
            pos: []
        }
    },
    methods: {
        agree() {
            axios.delete(`https://jsonplaceholder.typicode.com/posts/${this.$props.id}`).then((res) => {
                this.pos = this.$props.posts;
                this.pos = this.pos.filter((ele) => ele.id !== this.$props.id)
                this.$emit("updatePosts", this.pos);
            }).catch((err) => {
                console.log(err);
            })
        },
    },
    props: ['posts', 'id'],
}
</script>
<style>
.v-application .red {

    color: red !important;
    margin: 0 !important;
    padding: 0 !important;
    background: none !important;
    border: none !important;
    outline: none !important;
}

.v-btn--is-elevated {
    box-shadow: none !important;
}
</style>