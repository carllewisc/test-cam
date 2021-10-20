<template>
  <div class="d-contents">
    <div class="card author-box">
      <div class="card-body" style="margin-top: 100px">
        <div class="author-box-center text-center">
          <img
            alt="image"
            :src="`https://api.zeye.io/persons/${person.id}/photo`"
            class="rounded-circle shadow mx-auto d-block"
            style="max-width: 220px;"
          />
          <div class="clearfix"></div>
          <div class="author-box-name">
            <p class="mb-0">{{ fullName }}</p>
          </div>
          <div class="author-box-job">
            {{ person.organization.name ? person.identification_number : "" }}
          </div>
          <div class="author-box-job">
            {{ person.gender == "M" ? "Masculino" : "Femenino" }}
          </div>
        </div>
      </div>
      <div class="card-header">
        <h4>Información Laboral</h4>
      </div>
      <div class="card-body py-0">
        <div>
          <p class="clearfix">
            <span class="float-left"> Logotipo </span>
            <span class="float-right">
              <img
                alt="image"
                :src="
                  `https://api.zeye.io/organizations/${person.organization.id}/logo`
                "
                class="mr-3"
                width="120"
              />
            </span>
          </p>
          <p class="clearfix">
            <span class="float-left"> Empresa </span>
            <span class="float-right text-muted">
              {{ person.organization.name }}
            </span>
          </p>
          <p class="clearfix">
            <span class="float-left"> R.I.F. </span>
            <span class="float-right text-muted">
              {{ person.organization.rif }}
            </span>
          </p>
          <p class="clearfix">
            <span class="float-left"> Descripción </span>
            <span class="float-right text-muted">
              {{ person.organization.description }}
            </span>
          </p>
        </div>
        <div>
          <p class="clearfix">
            <span class="float-left"> Departamento </span>
            <span class="float-right text-muted">
              {{ person.division ? person.division.name : "" }}
            </span>
          </p>
        </div>
        <div>
          <p class="clearfix">
            <span class="float-left"> Cargo </span>
            <span class="float-right text-muted">
              {{ person.division ? person.division.description : "" }}
            </span>
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    person: {
      type: Object,
      required: true,
    },
  },
  computed: {
    fullName() {
      console.log(this.person);
      return `${this.person.names} ${this.person.surnames}`;
    },
  },
};
</script>

<style scoped>
@import "../assets/bootstrap.css";
</style>
