<template>
    <v-form ref="form" v-model="valid" lazy-validation>
        <v-text-field v-model="name" :counter="18" :rules="nameRules" label="ваше имя" required
            ref="name"></v-text-field>

        <v-text-field v-model="email" :rules="emailRules" label="E-mail" required ref="email"></v-text-field>
        <p>пол</p>
        <v-radio-group v-model="gender" mandatory>
            <v-radio label="мужской" value="male"></v-radio>
            <v-radio label="женский" value="female"></v-radio>
        </v-radio-group>
        <v-textarea v-model="message" outlined :counter="185" :rules="messageRules"></v-textarea>

        <v-checkbox ref="agree" v-model="checkbox" label="Согласен на обработку персональных данных ?"></v-checkbox>

        <v-row justify="end">
            <v-btn right color="warning" @click="validate">
                представить
            </v-btn>
        </v-row>
    </v-form>
</template>
<script>

export default {
    components: {
    },
    data: () => ({
        valid: true,
        name: '',
        nameRules: [
            v => !!v || 'Имя обязательно',
            v => (v && v.length <= 18) || 'Имя должно содержать менее 18 символов',
        ],
        email: '',
        emailRules: [
            v => !!v || 'E-mail is required',
            v => /.+@.+\..+/.test(v) || 'E-mail must be valid',
        ],
        checkbox: '',
        gender: '',
        message: '',
        messageRules: [v => v.length <= 185 || 'Max 185 characters'],
        formData: [],
    }),

    methods: {
        validate(e) {
            this.formData = [this.$data.name, this.$data.email, this.$data.gender, this.$data.message, this.$data.checkbox ? true : false]
            this.$emit("passData", this.formData)
            this.$refs.form.reset();
        },
    },

}
</script>
<style>
.v-input--radio-group--column .v-radio:not(:last-child):not(:only-child) {
    margin-bottom: 0px !important;
}

.v-input--radio-group--column .v-input--radio-group__input {
    flex-direction: row;
    gap: 15px;
    align-items: center;
    justify-content: flex-start;
}

.theme--light.v-btn.v-btn--has-bg {
    background: none !important;
    border: 1px dashed black !important;
    color: #58c658 !important;
    padding: 11px !important;
}

.row.justify-end {
    display: flex;
    justify-content: flex-end;
    align-items: flex-end;
    width: 100%;
}
</style>