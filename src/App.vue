<template>
  <div class="app">
    <div class="form-container">
      <div class="form-wrapper">
        <SheetForm :formData="formData1" @update:formData="updateFormData1" />
        <button :disabled="areFormsEqual" @click="syncToForm2">Синхронизировать</button>
      </div>
      <div class="form-wrapper">
        <SheetForm :formData="formData2" @update:formData="updateFormData2" />
        <button :disabled="areFormsEqual" @click="syncToForm1">Синхронизировать</button>
      </div>
    </div>
  </div>
</template>

<script>
import SheetForm from './components/SheetForm.vue';

export default {
  components: {
    SheetForm
  },
  data() {
    return {
      formData1: {
        name: '',
        age: '',
        height: '',
        gender: '',
        isMasterCharacter: false,
        race: '',
        class: '',
        skills: [],
        hairColor: '#000000',
        biography: ''
      },
      formData2: {
        name: '',
        age: '',
        height: '',
        gender: '',
        isMasterCharacter: false,
        race: '',
        class: '',
        skills: [],
        hairColor: '#000000',
        biography: ''
      }
    };
  },

 computed: {
    areFormsEqual() {
      return JSON.stringify(this.formData1) === JSON.stringify(this.formData2);
    }
  },

  methods: {
    syncToForm1() {
      this.formData1 = { ...this.formData2 };
    },
    syncToForm2() {
      this.formData2 = { ...this.formData1 };
    },
    updateFormData1(newData) {
      this.formData1 = newData;
    },
    updateFormData2(newData) {
      this.formData2 = newData;
    }
  }
};
</script>

<style>
.form-container {
  display: flex;
  justify-content: space-between;
}
.form-wrapper {
  margin: 20px;
}
.form-wrapper button {
  display: block;
  margin-top: 10px;
}
</style>