<template>
  <v-container>
    <v-layout>
  <v-row align="center">
    <v-row justify="space-around">
      <v-img
      src="https://praxisacademy.id/img/praxisnew.png"
      lazy-src="https://praxisacademy.id/img/praxisnew.png"
      aspect-ratio="1"
      max-width="300"
      max-height="300"
    ></v-img>
    </v-row>
    
    <v-form
      ref="form"
      v-model="valid"
      :lazy-validation="lazy"
    >
      <v-text-field
        v-model="id"
        :counter="10"
        :rules="idRules"
        label="Masukkan Id"
        required
      ></v-text-field>

      <v-text-field
        v-model="code"
        :counter="3"
        :rules="codeRules"
        label="Masukkan Kode"
        required
      ></v-text-field>

      <v-select
        v-model="select"
        :items="items"
        :rules="[v => !!v || 'Kelas is required']"
        label="Pilihan Kelas"
        required
      ></v-select>

      <v-checkbox
        v-model="checkbox"
        :rules="[v => !!v || 'You must agree to continue!']"
        label="Do you agree?"
        required
      ></v-checkbox>

      <v-btn
        :disabled="!valid"
        color="success"
        class="mr-4"
        @click="validate"
      >
        Validate
      </v-btn>

      <v-btn
        color="error"
        class="mr-4"
        @click="reset"
      >
        Reset Form
      </v-btn>

      <v-btn
        color="warning"
        @click="resetValidation"
      >
        Reset Validation
      </v-btn>
    </v-form>
  </v-row>
    </v-layout>
  </v-container>
</template>

<script>
  export default {
    data: () => ({
      valid: true,
      id: '',
      idRules: [
        v => !!v || 'Id is required',
        v => (v && v.length <= 10) || 'Id must be less than 10 characters',
      ],
      code: '',
      codeRules: [
        v => !!v || 'Kode is required',
        v => (v && v.length <= 3) || 'Code must be valid',
      ],
      select: null,
      items: [
        'Kelas 1',
        'Kelas 2',
        'Kelas 3',
        'Kelas 4',
        'Kelas 5',
        'Kelas 6',
        'Kelas 7',
        'Kelas 8',
        'Kelas 9',
        'Kelas 10',
        'Kelas 11',
        'Kelas 12',
      ],
      checkbox: false,
      lazy: false,
    }),
    methods: {
      validate () {
        if (this.$refs.form.validate()) {
          this.snackbar = true
        }
      },
      reset () {
        this.$refs.form.reset()
      },
      resetValidation () {
        this.$refs.form.resetValidation()
      },
    },
  }
</script>
