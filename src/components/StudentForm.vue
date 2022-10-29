<template>
  <v-app class="v-app">
    <v-form ref="form" v-model="valid" lazy-validation class="form">
      <div>
        <font-awesome-icon icon="fa-brands fa-github" />
        <h1>ficha de inscrição estudantil</h1>
      </div>
      <v-text-field
        v-model="name"
        :counter="100"
        :rules="nameRules"
        label="Nome"
        required
      ></v-text-field>

      <v-text-field
        v-model="RA"
        label="RA"
        :rules="raRules"
        required
      ></v-text-field>

      <v-text-field
        v-model="Turma"
        :rules="turmaRules"
        label="Turma"
        required
      ></v-text-field>

      <v-text-field
        v-model="CPF"
        :rules="cpfRules"
        label="CPF"
        required
        id="cpf_digitado"
      ></v-text-field>

      <div style="">
        <v-btn
          :disabled="!valid"
          color="success"
          class="mr-4"
          @click="validate"
          style="padding: 10gap; margin: 10px"
        >
          Validate
        </v-btn>
        <v-btn color="error" class="mr-4" @click="reset"> Reset Form </v-btn>
        <v-spacer />
        <v-btn color="warning" @click="resetValidation">
          Reset Validation
        </v-btn>
      </div>
    </v-form>
    <div class="cpfValidation">
      <div id="success" style="display: none">
        <strong>Oba!</strong> Seu CPF é válido
      </div>
      <div id="error" style="display: none">
        <strong>Ops!</strong> Seu CPF não é válido
      </div>
      <div id="incompleteCPF" style="display: none">
        <strong>Ops!</strong> Seu CPF esta incompleto
      </div>
    </div>
  </v-app>
</template>

<script>
export default {
  name: "StudentForm",

  data: () => ({
    valid: true,
    name: "Samuel Barbosa Almeida",
    nameRules: [
      (nome) => !!nome || "Informe um Nome",
      (nome) =>
        (nome && nome.length <= 100) || "Name must be less than 100 characters",
    ],
    Turma: "",
    turmaRules: [(turma) => !!turma || "Informe uma turma"],
    RA: "",
    raRules: [(ra) => !!ra || "Informe um RA"],
    CPF: "",
    cpfRules: [
      (cpf) => !!cpf || "Informe um CPF",
      // (cpf) => /^\d{3}\.\d{3}\.\d{3}-\d{2}$/.test(cpf) || "CPF must be valid",
    ],
  }),

  methods: {
    reset() {
      this.$refs.form.reset();
    },
    resetValidation() {
      this.$refs.form.resetValidation();
    },

    validate() {
      this.$refs.form.validate();
      document.getElementById("success").style.display = " none";
      document.getElementById("error").style.display = "none";
      document.getElementById("incompleteCPF").style.display = "none";

      const cpf = document.getElementById("cpf_digitado").value;
      const resultadoValidacao = this.validaCPF(cpf);

      if (resultadoValidacao == true) {
        document.getElementById("success").style.display = " block";
      }
      if (resultadoValidacao == false) {
        document.getElementById("error").style.display = "block";
      }
      if (resultadoValidacao == "CPF incompleto") {
        document.getElementById("incompleteCPF").style.display = "block";
      }
    },

    validaCPF(cpf) {
      if (cpf.length != 11) {
        return "CPF incompleto";
      } else {
        var numeros = cpf.substring(0, 9);
        var digitos = cpf.substring(9);
        var soma = 0;
        for (var i = 10; i > 1; i--) {
          soma += numeros.charAt(10 - i) * i;
        }

        var resultado = soma % 11 < 2 ? 0 : 11 - (soma % 11);

        if (resultado != digitos.charAt(0)) {
          return false;
        }

        soma = 0;
        numeros = cpf.substring(0, 10);
        for (var k = 11; k > 1; k--) {
          soma += numeros.charAt(11 - k) * k;
        }

        resultado = soma % 11 < 2 ? 0 : 11 - (soma % 11);
        console.log(resultado);
        if (resultado != digitos.charAt(1)) {
          return false;
        }
        return true;
      }
    },
  },
};
</script>

<style>
@media only screen and (max-width: 500px) {
  v-app {
    margin: auto;
    max-width: 400px;
    position: relative;
    display: flex;
  }
  .form {
    max-width: 290px;
  }
}

.form {
  width: 500px;
  position: relative;
  margin: auto;
}

.cpfValidation {
  width: 500px;
  position: relative;
  margin: auto;
  margin-top: 5px;
}
</style>
