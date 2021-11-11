<template>
  <v-container>
    <v-row class="text-left">
      <v-col cols="12">
        <h2>Projects</h2>
      </v-col>
      <v-col cols="12">
        <v-data-table
            v-model="selected"
            :headers="headers"
            :items="items"
            class="elevation-1"
            hide-default-footer
        >
          <template v-slot:item.actions="{ item }">
            <v-btn color="primary" small
                @click="planTeam(item['name'])"
            >
              Find
            </v-btn>
          </template>
        </v-data-table>
      </v-col>
    </v-row>

    <v-row class="text-left" v-if="team !== undefined & team.length > 0">
      <v-col cols="12">
        <h3>Team details</h3>
      </v-col>
      <v-col cols="12">
        <v-data-table
            :headers="teamHeaders"
            :items="team"
            hide-default-footer
        >
        </v-data-table>
      </v-col>
    </v-row>

  </v-container>
</template>

<script>
export default {
  name: 'HelloWorld',

  data: () => ({
    headers: [
      {text: 'id', value: 'id'},
      {text: 'Project name', value: 'name'},
      {text: 'Customer', value: 'customer'},
      {text: 'Deadline', value: 'deadline'},
      {text: 'Skills', value: 'skills'},
      {text: '', value: 'actions'}
    ],
    teamHeaders: [
      {text: 'First Name', value: 'firstname'},
      {text: 'Last Name', value: 'lastname'},
      {text: 'Skills', value: 'skills'}
    ],
    items: [
      {"id":1, "name": "ABCD-1", "customer":"IKEA", "deadline": "2 months", "skills": "Java, Javascript, PostgreSQL, Terraform, GCP"},
      {"id":2, "name": "ABCD-2", "customer":"IKEA", "deadline": "1 months", "skills": "Python, GCP, Cloud Functions"},
    ],
    employees: [
      {"lastname":"Green", "firstname": "John", "skills": ["Java"]},
      {"lastname":"Samuel", "firstname": "Steven", "skills": ["Javascript"]},
      {"lastname":"Blue", "firstname": "Georgia", "skills": ["PostgreSQL"]},
      {"lastname":"Emmerson", "firstname": "Anne", "skills": ["Terraform", "GCP"]},
      {"lastname":"Red", "firstname": "Bill", "skills": ["Cloud Function", "GCP"]},
      {"lastname":"Plumb", "firstname": "Donald", "skills": ["Python"]},
    ],
    selected: undefined,
    team: []
  }),
  methods: {
    planTeam(name) {
      if (name === 'ABCD-1') {
        this.team = [
          {"lastname":"Green", "firstname": "John", "skills": ["Java"]},
          {"lastname":"Samuel", "firstname": "Steven", "skills": ["Javascript"]},
          {"lastname":"Blue", "firstname": "Georgia", "skills": ["PostgreSQL"]},
          {"lastname":"Emmerson", "firstname": "Anne", "skills": ["Terraform", "GCP"]}
        ]
      } else {
        this.team = [
          {"lastname":"Red", "firstname": "Bill", "skills": ["Cloud Function", "GCP"]},
          {"lastname":"Plumb", "firstname": "Donald", "skills": ["Python"]}]
      }
    }
  }
}
</script>
