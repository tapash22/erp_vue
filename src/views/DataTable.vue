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

        <v-card-text>
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

    <v-row>
      <v-col>
        <v-card>
          <v-card-text>
            <div class="d-flex justify-start">
              <div class="box w-25 h-25 d-block pa-2 red lighten-4 rounded-sm ">
                <span class="text-body-1 font-weeight-bold pa-1">01</span>
                <p class="font-medium text-body-2">Date:<span class="text-caption font-weight-normal">01-04-2023</span>
                </p>
                <p class="font-medium text-body-2">Time:<span class="text-caption font-weight-normal">08:30 pm</span></p>
              </div>
              <p>
                Lorem ipsum dolor, sit amet consectetur adipisicing elit. Voluptate excepturi inventore vitae numquam quod
                perspiciatis nesciunt pariatur aliquam esse officiis et dicta asperiores maiores cum impedit deleniti,
                ratione corporis distinctio, beatae maxime ipsum veniam amet! Quam non magnam maiores voluptas velit
                tenetur temporibus quia, incidunt est nesciunt ratione illum fuga! Magnam molestias in explicabo
                consectetur. Ut saepe doloribus ipsam ipsum, quasi autem laudantium doloremque nesciunt temporibus
                aspernatur perferendis voluptatum quo nobis quam dignissimos, similique nam impedit ducimus repellat velit
                soluta maxime corporis nemo? Natus dicta tempore aspernatur laborum est ad error facere et, quaerat animi
                libero architecto. Perferendis maxime consequuntur soluta fugit, iure, molestias tenetur quam sed rerum
                assumenda tempore debitis ea adipisci minus. Cum sint, odit possimus error quae expedita exercitationem
                optio vel. Fuga, suscipit, voluptatum repellendus doloribus ullam assumenda numquam molestiae qui dolorem
                modi quis porro ducimus aliquid neque aspernatur nulla adipisci earum eligendi odio incidunt. Quam
                perferendis nostrum iusto necessitatibus quasi fugiat totam est, minima impedit consequuntur. Assumenda
                et, enim molestiae illum inventore quis ducimus aspernatur ipsa nihil incidunt consequatur optio ipsam
                qui? Sit beatae, aspernatur atque consectetur consequuntur, minima asperiores explicabo placeat amet
                inventore fugiat fuga pariatur modi saepe velit sunt aut ipsum tenetur sapiente vel dolore? Id magnam
                culpa odit, mollitia eos deleniti aspernatur dolore sit quis ex voluptatum, reiciendis a nulla et sunt
                aliquam! Corrupti sit fuga cupiditate suscipit totam inventore quia modi, fugiat ut vel dolorum labore qui
                eos accusantium, doloremque reprehenderit cumque similique impedit quas blanditiis ipsa veniam!
                Accusantium doloribus ipsam eius quod, distinctio repellendus architecto nihil a laboriosam harum dolore.
                Quidem excepturi architecto quaerat ullam ex ipsa placeat nulla quisquam molestias inventore qui suscipit
                et, voluptatem adipisci amet recusandae optio odio quibusdam. Similique porro dolor distinctio quae iusto
                sint esse animi nemo non, mollitia laboriosam ullam odit earum aperiam, id unde quas provident optio nulla
                iste nobis a quisquam! Amet officiis id voluptatem nesciunt iste architecto alias voluptate veritatis.
                Perspiciatis enim tenetur vitae, optio impedit nulla consectetur ipsam itaque, suscipit sit molestias at
                explicabo. Magni eveniet recusandae consequuntur qui alias. Praesentium cumque qui corporis vel beatae
                quam fuga, suscipit soluta libero nulla eos maxime, rerum quia aperiam. Assumenda nihil temporibus,
                perspiciatis odio illo aperiam rerum minus libero. Expedita aliquid eveniet quam necessitatibus minima
                sapiente perferendis explicabo deserunt totam quos? Odio, quidem nisi ex cupiditate ut aperiam consequatur
                officiis, blanditiis veniam non natus culpa commodi praesentium, unde totam perferendis eligendi repellat
                sapiente! Quam velit temporibus labore vitae! Voluptates, hic ipsa. Pariatur atque voluptatibus tempora
                officiis voluptate. Rem explicabo hic ducimus possimus eius omnis quam nemo iste a dolores voluptas
                nesciunt perferendis facere inventore accusamus, dolore eaque amet suscipit quod sequi asperiores vero
                doloribus quo necessitatibus! Unde est in neque eveniet ipsam ullam explicabo, modi suscipit, maiores
                possimus provident labore sapiente? Similique cumque illum nulla magnam dolore fugiat, saepe eaque est
                tenetur vero optio praesentium voluptatibus autem! Debitis eaque aliquam aut, reprehenderit molestiae vel
                veritatis voluptates nulla aspernatur quis corporis magnam dolores esse saepe sequi quaerat tempore veniam
                sed aliquid explicabo optio consequatur alias culpa consequuntur! Quaerat dolores id atque aliquam tempora
                tenetur nulla cum aut! Iusto doloribus deserunt quae, natus rerum non perspiciatis ipsa aspernatur sit
                accusamus dignissimos odio recusandae eligendi distinctio dolore! Ipsum blanditiis minus aut fugit amet
                nemo quaerat atque necessitatibus asperiores aperiam quas quia a, perspiciatis inventore iusto neque sequi
                incidunt ut eaque natus autem. Et dolorum enim illum hic, expedita error quam dicta libero voluptatum
                earum repellendus cum eligendi natus commodi, dolorem sit ipsa totam, aliquam explicabo consequuntur
                laboriosam delectus quaerat. Maxime doloremque laboriosam impedit et, qui error quo dolores harum. Nostrum
                accusamus iusto recusandae ea modi, assumenda, optio alias minima tenetur fugiat repellendus obcaecati
                possimus corporis quod quasi, omnis quisquam. Voluptate vitae quae voluptatem laudantium temporibus quos
                neque incidunt optio adipisci consequuntur ratione, deleniti sint quisquam corporis nam ipsum labore error
                doloribus facilis officia vero culpa nostrum veniam magni. Perspiciatis, voluptate! Adipisci laborum
                deleniti, recusandae placeat ipsum sit earum fugit. Eveniet provident beatae tempora recusandae delectus
                impedit inventore alias sunt nesciunt perspiciatis numquam, nisi repellendus fuga ab sapiente a nemo
                consectetur, blanditiis quibusdam! Aspernatur harum expedita voluptatibus dolorum, qui, et vero saepe nisi
                dicta tempore facere quis quo similique repellat. Corrupti natus quasi ab. Iure nam, commodi non repellat
                recusandae nihil debitis accusantium error exercitationem, eaque molestias delectus vitae doloribus modi
                sit vero veniam adipisci necessitatibus nobis qui incidunt repellendus pariatur fuga officiis! Aliquam
                soluta dolores sed ad dolor repudiandae cumque cum quibusdam ipsum asperiores quae, sint minima reiciendis
                quod delectus excepturi facilis aliquid quia mollitia vel unde! Iure excepturi atque repudiandae nemo
                explicabo tempore impedit ut, voluptas laborum deserunt dolor quos earum voluptatem delectus assumenda
                accusantium sequi officiis ad quas pariatur itaque tempora ipsa error ea. Autem eveniet reprehenderit
                officiis illo exercitationem porro odio! Autem nobis, dicta quos sunt repellendus provident eius, iusto
                ducimus aut a nesciunt quibusdam quo cupiditate quas nisi harum? Quaerat amet officiis soluta sed quis
                facere ipsam. Voluptas fugit explicabo, maxime dolores aliquid optio voluptatibus debitis dolor, dolorem
                accusantium soluta laborum impedit assumenda cupiditate voluptates libero facilis consequuntur nam ex qui
                magnam. Quidem rerum excepturi molestiae accusamus in, fugit necessitatibus repellat libero quis
                perferendis illum saepe. Architecto unde animi dignissimos, obcaecati facilis corrupti. Consequuntur
                exercitationem beatae molestiae, fugiat at libero, distinctio odit explicabo voluptate tenetur mollitia
                consequatur possimus voluptatibus in officia odio dolorum laboriosam consectetur ullam quia, nulla
                praesentium veritatis suscipit? A, non nobis. Maiores ipsa inventore voluptates facilis dolores labore
                cumque iure, cupiditate voluptate nobis? Quibusdam saepe provident tempore, sint explicabo iste at
                deserunt odio delectus nisi enim consectetur veniam repellendus inventore ipsam eum sequi tenetur ipsum
                voluptatibus harum temporibus sit cupiditate. Voluptas nisi accusamus omnis esse excepturi nam doloribus
                eius distinctio dolor velit molestias veniam inventore provident officia incidunt, dolores architecto sunt
                sequi officiis delectus fugit. Unde voluptates doloremque tempora corporis reiciendis beatae vero ullam
                quaerat dolorum fugiat, sit, soluta excepturi ratione non deserunt temporibus est nihil exercitationem,
                mollitia at quisquam. Repellat quos sunt, voluptatibus illum dolorum placeat mollitia neque, nesciunt
                nihil, alias ullam totam hic unde adipisci quis inventore.
              </p>
            </div>
          </v-card-text>
        </v-card>
      </v-col>
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
      const headersTmp = this.headers;
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

.light::-webkit-scrollbar {
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
}

/* @media screen and (max-width: 400px) {
  .v-data-table > .v-data-table__wrapper .v-data-table__mobile-table-row {
    overflow: scroll;
  }
} */</style>
