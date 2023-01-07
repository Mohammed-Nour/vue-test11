<template>
  <div>
    <h1>Добавить запись</h1>
    <div class="par">
      <div class="pareee">
        <FormVue @passData="GetData($event)" />
      </div>
      <div v-if="active" id="sec" :class="{ active: active }">
        <div class="label">name: {{ dataForm[0] }}</div>
        <div class="label">email: {{ dataForm[1] }}</div>
        <div class="label">gender: {{ dataForm[2] }}</div>
        <div class="label">message: {{ dataForm[3] }}</div>
        <div class="label">agree: {{ dataForm[4] }}</div>
      </div>
    </div>
  </div>

</template>

<script>
import FormVue from '@/components/Form.vue';

export default {
  name: 'Create',
  components: {
    FormVue
  },
  data() {
    return {
      dataForm: [],
      dataLabel: ["name", "email", "gender", "message", "agree"],
      active: false,
    }

  },
  methods: {
    GetData(data) {
      this.dataForm = data;
      this.active = true;
    },
  },
}
</script>
<style>
.par {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  gap: 10px;
}

.label {
  color: rgb(104, 101, 101);
}

.pareee {
  background-color: white;
  padding: 25px;
  border-radius: 5px;
  margin-top: 30px;
  width: 50%;
  height: fit-content;
}

#sec {
  display: none;
  height: 570px;
  padding: 25px;
  border-radius: 5px;
  margin-top: 30px;
  width: 50%;
  background-color: white;
  border: 3px dashed black;
}

.active {
  display: block !important;
}
</style>