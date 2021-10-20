<template>
  <div class="d-contents">
    <div class="card author-box">

      <div class="card-body">
        <div class="author-box-center">
          <img
              alt="image"
              :src="`https://api.zeye.io/persons/${person.id}/photo`"
              class="rounded-circle shadow"
              style="max-width: 220px;"
          />
          <div class="clearfix"></div>
          <div class="author-box-name">
            <p class="mb-0">{{ fullName }}</p>
          </div>
          <div class="author-box-job">
            {{
              person.organization.name
                  ? person.organization.name
                  : ""
            }}
          </div>
          <div class="author-box-job">
            {{
              person.position
                  ? person.position.title
                      ? person.position.title
                      : ""
                  : ""
            }}
          </div>
        </div>
      </div>
      <!-- <div class="card-header">
        <h4>Organización</h4>
      </div> -->
      <div class="card-body py-0">
        <div>
          <p class="clearfix">
            <!-- <span class="float-left"> Logotipo </span> -->
            <span class="float-right">
              <img
                  alt="image"
                  :src="`https://api.zeye.io/organizations/${person.organization.id}/logo`"
                  class="mr-3"
                  width="120"
              />
            </span>
          </p>
          <!-- <p class="clearfix">
            <span class="float-left"> Nombre </span>
            <span class="float-right text-muted">
              {{ person.organization.name }}
            </span>
          </p> -->
          <p class="clearfix">
            <!-- <span class="float-left"> R.I.F. </span> -->
            <span class="float-right text-muted">
              {{ person.organization.rif }}
            </span>
          </p>
          <p class="clearfix">
            <!-- <span class="float-left"> Descripción </span> -->
            <span class="float-right text-muted">
              {{ person.organization.description }}
            </span>
          </p>
        </div>
      </div>

      <div class="card-header">
        <!-- <h4>División</h4> -->
      </div>
      <div class="card-body py-0">
        <div>
          <p class="clearfix">
            <!-- <span class="float-left"> Nombre </span> -->
            <span class="float-right text-muted">
              {{ person.division ? person.division.name : "" }}
            </span>
          </p>
        </div>
        <div>
          <p class="clearfix">
            <!-- <span class="float-left"> Descripción </span> -->
            <span class="float-right text-muted">
              {{ person.division ? person.division.description : "" }}
            </span>
          </p>
        </div>
      </div>

      <div class="card-header">
        <!-- <h4>Sucursal</h4> -->
      </div>
      <div class="card-body py-0">
        <div>
          <p class="clearfix">
            <!-- <span class="float-left"> Dirección </span> -->
            <span class="float-right text-muted">
              {{ person.division ? person.division.subsidiary.address : "" }}
            </span>
          </p>
        </div>
        <div>
          <p class="clearfix">
            <!-- <span class="float-left"> Nombre </span> -->
            <span class="float-right text-muted">
              {{ person.division ? person.division.subsidiary.name : "" }}
            </span>
          </p>
        </div>
        <div>
          <p class="clearfix">
            <!-- <span class="float-left"> Descripción </span> -->
            <span class="float-right text-muted">
              {{
                person.division ? person.division.subsidiary.description : ""
              }}
            </span>
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export  default  {
  props: {
    person: {
      type: Object,
      required: true,
    },
  },
  computed: {
    fullName() {
      console.log(this.person)
      return `${this.person.names} ${this.person.surnames}`;
    },
  },
}
</script>

<style scoped>
@import '../assets/bootstrap.css';
</style>

