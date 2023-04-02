<template>
  <v-container>
    <v-row class="d-flex justify-center pt-2">
      <v-card elevation="0">
        <v-card-title class=" d-sm-block d-md-flex justify-space-between ">

          <h2 class="font text-h6 text-uppercase font-weight-bold pb-5 d-flex justify-start">Information Details</h2>
          <!-- <v-spacer></v-spacer> -->

          <div class="select-box">
            <v-select v-model="selectedHeaders" :items="headers" label="Select Columns" multiple solo rounded
              return-object class="font text-body-1 font-weight-normal font">
              <template v-slot:selection="{ item, index }">
                <v-chip small v-if="index < 1" color="red lighten-2 white--text ">
                  <span class="font text-caption white--text font-weight-normal">{{ item.text }}</span>
                </v-chip>
                <span v-if="index === 2" class="grey--text font font-weight-normal text-caption">(+{{
                  selectedHeaders.length - 2 }} others)</span>
              </template>
            </v-select>
          </div>
        </v-card-title>

        <v-card-text >
          <v-data-table :headers="showHeaders" :items="desserts" hide-default-footer
            v-sortable-table="{ onEnd: sortTheHeadersAndUpdateTheKey }" :key="anIncreasingNumber" class="light"
            mobile-breakpoint="0">
            <template v-slot:item.actions="{ item }">
              <v-icon small class="mr-2"> mdi-pencil </v-icon>
              <v-icon small> mdi-delete </v-icon>
            </template>
          </v-data-table>
        </v-card-text>
      </v-card>
    </v-row>

  </v-container>
</template>

<script>
import {
  Sortable
} from "sortablejs";

function watchClass(targetNode, classToWatch) {
  let lastClassState = targetNode.classList.contains(classToWatch);
  const observer = new MutationObserver((mutationsList) => {
    for (let i = 0; i < mutationsList.length; i++) {
      const mutation = mutationsList[i];
      if (
        mutation.type === "attributes" &&
        mutation.attributeName === "class"
      ) {
        const currentClassState =
          mutation.target.classList.contains(classToWatch);
        if (lastClassState !== currentClassState) {
          lastClassState = currentClassState;
          if (!currentClassState) {
            mutation.target.classList.add("sortHandle");
          }
        }
      }
    }
  });
  observer.observe(targetNode, {
    attributes: true
  });
}

export default {
  data: () => ({
    anIncreasingNumber: 1,
    headers: [{
      text: "SL. No",
      value: "id"
    },
    {
      text: "Project Name",
      value: "ProjectName"
    },
    {
      text: "Client Name",
      value: "ClientName"
    },
    {
      text: "Project Value",
      value: "ProjectValue"
    },
    {
      text: " Project Manager",
      value: "ProjectManager"
    },
    {
      text: "Start Date",
      value: "StartDate"
    },
    {
      text: "Expected Deadline",
      value: "ExpectedDeadline"
    },
    {
      text: "Actual Project Completion Date",
      value: "ProjectCompletionDate",
    },
    {
      text: " Estimated Hours",
      value: "EstimatedHours"
    },
    {
      text: "Total Logged Hours",
      value: "TotalLoggedHours"
    },
    {
      text: "Tasks",
      value: "Tasks"
    },
    {
      text: "Milestones",
      value: "Milestones"
    },
    {
      text: "Payment",
      value: "Payment"
    },
    {
      text: "Progress",
      value: "Progress"
    },
    {
      text: "Deliverable Status",
      value: "DeliverableStatus"
    },
    {
      text: "Project Status",
      value: "ProjectStatus"
    },
    {
      text: "Actions",
      value: "actions",
      sortable: false
    },
    ],
    desserts: [],
    selectedHeaders: [],
    tableHeader: [],
  }),

  created() {
    this.initialize();
    this.tableHeader = Object.values(this.headers);
    this.selectedHeaders = this.tableHeader;
  },

  computed: {
    //Done to get the ordered headers
    showHeaders() {
      return this.headers.filter((s) => this.selectedHeaders.includes(s));
    },
  },

  methods: {
    initialize() {
      this.desserts = [{
        id: 1,
        ProjectName: "Riadus Salehin",
        ClientName: "Riadus Salehin",
        ProjectValue: "44",
        ProjectManager: "Riadus Salehin",
        StartDate: new Date().toLocaleDateString(),
        ExpectedDeadline: new Date().toLocaleDateString(),
        ProjectCompletionDate: new Date().toLocaleDateString(),
        EstimatedHours: "12h",
        TotalLoggedHours: new Date().toLocaleTimeString(),
        Tasks: 5,
        Milestones: 10,
        Payment: true,
        Progress: true,
        DeliverableStatus: "pending",
        ProjectStatus: "done",
      },
      {
        id: 2,
        ProjectName: "Riadus Salehin",
        ClientName: "Riadus Salehin",
        ProjectValue: "44",
        ProjectManager: "Riadus Salehin",
        StartDate: new Date().toLocaleDateString(),
        ExpectedDeadline: new Date().toLocaleDateString(),
        ProjectCompletionDate: new Date().toLocaleDateString(),
        EstimatedHours: "12h",
        TotalLoggedHours: new Date().toLocaleTimeString(),
        Tasks: 5,
        Milestones: 10,
        Payment: true,
        Progress: true,
        DeliverableStatus: "pending",
        ProjectStatus: "done",
      },
      {
        id: 3,
        ProjectName: "Riadus Salehin",
        ClientName: "Riadus Salehin",
        ProjectValue: "44",
        ProjectManager: "Riadus Salehin",
        StartDate: new Date().toLocaleDateString(),
        ExpectedDeadline: new Date().toLocaleDateString(),
        ProjectCompletionDate: "02/04/2023",
        EstimatedHours: "12h",
        TotalLoggedHours: new Date().toLocaleTimeString(),
        Tasks: 5,
        Milestones: 10,
        Payment: true,
        Progress: true,
        DeliverableStatus: "pending",
        ProjectStatus: "done",
      },
      ];
    },

    sortTheHeadersAndUpdateTheKey(evt) {
      const headersTmp = this.showHeaders;
      const oldIndex = evt.oldIndex;
      const newIndex = evt.newIndex;
      if (newIndex >= headersTmp.length) {
        let k = newIndex - headersTmp.length + 1;
        while (k--) {
          headersTmp.push(undefined);
        }
      }
      headersTmp.splice(newIndex, 0, headersTmp.splice(oldIndex, 1)[0]);
      this.table = headersTmp;
      this.anIncreasingNumber += 1;
    },
  },

  directives: {
    "sortable-table": {
      inserted: (el, binding) => {
        el.querySelectorAll("th").forEach((draggableEl) => {
          watchClass(draggableEl, "sortHandle");
          draggableEl.classList.add("sortHandle");
        });
        Sortable.create(
          el.querySelector("tr"),
          binding.value ? {
            ...binding.value,
            handle: ".sortHandle"
          } : {}
        );
      },
    },
  },
};
</script>

<style>.select-box {
  width: 250px;
  height: auto;
}

/* .light::-webkit-scrollbar {
  width: 10px;
}

.light::-webkit-scrollbar-track {
  background: #e6e6e6;
  border-left: 1px solid #dadada;
}

.light::-webkit-scrollbar-thumb {
  background: #616e80;
  border: solid 3px #e6e6e6;
  border-radius: 7px;
}

.light::-webkit-scrollbar-thumb:hover {
  background: #616e80;
} */

/* @media screen and (max-width: 400px) {
  .v-data-table > .v-data-table__wrapper .v-data-table__mobile-table-row {
    overflow: scroll;
  }
} */</style>
