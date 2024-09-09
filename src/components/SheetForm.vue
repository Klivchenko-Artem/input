<template>
  <div class="character-sheet-form">
    <label>
      Имя:
      <TextInput v-model="localFormData.name" @input="emitUpdate" />
    </label>
    <label>
      Возраст:
      <DateInput v-model="localFormData.age" @input="emitUpdate" />
    </label>
    <label>
      Рост:
      <NumberInput v-model="localFormData.height" @input="emitUpdate" />
    </label>
    <label>
      Пол:
      <RadioInput v-model="localFormData.gender" :options="genders" @change="emitUpdate" />
    </label>
    <label>
      Персонаж мастера?
      <CheckboxInput v-model="localFormData.isMasterCharacter" @change="emitUpdate" />
    </label>
    <label>
      Раса:
      <SelectInput v-model="localFormData.race" :options="races" @change="emitUpdate" />
    </label>
    <label>
      Класс:
      <SelectInput v-model="localFormData.class" :options="classes" @change="emitUpdate" />
    </label>
    <label>
      Таланты:
      <CheckboxListInput v-model="localFormData.skills" :options="skills" @change="emitUpdate" />
    </label>
    <label>
      Цвет волос:
      <ColorInput v-model="localFormData.hairColor" @input="emitUpdate" />
    </label>
    <label>
      Биография:
      <TextareaInput v-model="localFormData.biography" @input="emitUpdate" />
    </label>
  </div>
</template>

<script>
import TextInput from './TextInput.vue';
import DateInput from './DateInput.vue';
import NumberInput from './NumberInput.vue';
import RadioInput from './RadioInput.vue';
import CheckboxInput from './CheckboxInput.vue';
import SelectInput from './SelectInput.vue';
import CheckboxListInput from './CheckboxListInput.vue';
import ColorInput from './ColorInput.vue';
import TextareaInput from './TextareaInput.vue';

export default {
  components: {
    TextInput,
    DateInput,
    NumberInput,
    RadioInput,
    CheckboxInput,
    SelectInput,
    CheckboxListInput,
    ColorInput,
    TextareaInput
  },
  props: {
    formData: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      localFormData: { ...this.formData },
      genders: ['Мужской', 'Женский'],
      races: ['Человек', 'Эльф', 'Дворф', 'Орк'],
      classes: ['Воин', 'Маг', 'Лучник', 'Жрец'],
      skills: ['Сила', 'Ловкость', 'Интеллект', 'Выносливость']
    };
  },
  watch: {
    formData: {
      handler(newValue) {
        this.localFormData = { ...newValue };
      },
      deep: true
    }
  },
  methods: {
    emitUpdate() {
      this.$emit('update:formData', { ...this.localFormData });
    }
  }
};
</script>

<style scoped>
.character-sheet-form {
  margin: 20px;
}
.character-sheet-form label {
  display: block;
  margin-bottom: 15px;
}
</style>