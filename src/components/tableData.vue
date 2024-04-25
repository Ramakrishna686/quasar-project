<template>
  <div class="q-pa-md">
    <q-table
      flat
      bordered
      title="Table Data"
      :rows="rows"
      :columns="columns"
      row-key="fileId"
      v-model:pagination="pagination"
    >
      <template v-slot:pagination="scope">
        <q-btn
          v-if="scope.pagesNumber > 2"
          icon="first_page"
          color="grey-8"
          round
          dense
          flat
          :disable="scope.isFirstPage"
          @click="scope.firstPage"
        />

        <q-btn
          icon="chevron_left"
          color="grey-8"
          round
          dense
          flat
          :disable="scope.isFirstPage"
          @click="scope.prevPage"
        />

        <q-btn
          icon="chevron_right"
          color="grey-8"
          round
          dense
          flat
          :disable="scope.isLastPage"
          @click="scope.nextPage"
        />

        <q-btn
          v-if="scope.pagesNumber > 2"
          icon="last_page"
          color="grey-8"
          round
          dense
          flat
          :disable="scope.isLastPage"
          @click="scope.lastPage"
        />
      </template>
    </q-table>
  </div>
</template>

<script>
import { ref, computed } from "vue";

const apiResponse = {
    "content": [
        {
            "fileId": "3ec571bc-1760-4088-97fc-70da82e5796e",
            "userId": "b56ef446-99a1-4ade-87ae-5bae165ee7bd",
            "fileName": "Billing_Report_2024.23.04.csv",
            "status": "PENDING",
            "createdDate": "2024-04-23T16:50:58.785346+05:30"
        },
        {
            "fileId": "4bbcf5fa-2ad3-4856-8dc9-36109ad7e2f7",
            "userId": "b56ef446-99a1-4ade-87ae-5bae165ee7bd",
            "fileName": "Billing_Report_2024.23.04.csv",
            "status": "PENDING",
            "createdDate": "2024-04-23T17:05:13.315902+05:30"
        },
        {
            "fileId": "40f923ae-4a29-447a-9923-d17628891510",
            "userId": "b56ef446-99a1-4ade-87ae-5bae165ee7bd",
            "fileName": "Billing_Report_2024.23.04.csv",
            "status": "PENDING",
            "createdDate": "2024-04-23T17:21:13.545041+05:30"
        },
        {
            "fileId": "32669166-5bc7-49da-bb64-48a82a9ae43a",
            "userId": "b56ef446-99a1-4ade-87ae-5bae165ee7bd",
            "fileName": "Billing_Report_2024.23.04.csv",
            "status": "PENDING",
            "createdDate": "2024-04-23T17:33:18.063927+05:30"
        },
        {
            "fileId": "3d4916d7-36d9-43ae-b4f5-9ae3be785fcd",
            "userId": "b56ef446-99a1-4ade-87ae-5bae165ee7bd",
            "fileName": "Billing_Report_2024.23.04.csv",
            "status": "PENDING",
            "createdDate": "2024-04-23T18:11:10.779886+05:30"
        }
    ],
    "pageable": {
        "sort": {
            "unsorted": false,
            "sorted": true,
            "empty": false
        },
        "offset": 0,
        "pageNumber": 0,
        "pageSize": 10,
        "unpaged": false,
        "paged": true
    },
    "totalPages": 1,
    "totalElements": 5,
    "last": true,
    "size": 10,
    "number": 0,
    "sort": {
        "unsorted": false,
        "sorted": true,
        "empty": false
    },
    "numberOfElements": 5,
    "first": true,
    "empty": false
}

const columns = [
  {
    name: "desc",
    required: true,
    label: "File Id",
    align: "left",
    classes: 'customEllipsis',
    field: (row) => row.fileId,
    sortable: true,
  },
  {
    name: "userId",
    classes: 'customEllipsis',
    align: "center",
    label: "User Id",
    field: "userId",
    sortable: true,
  },
  { name: "fileName", label: "File Name", field: "fileName",
    classes: 'customEllipsis',
   sortable: true },
  { name: "status", label: "Status", field: "status" },
  { name: "createdDate", label: "Created Date", field: "createdDate" }
];

const rows = [ {
            "fileId": "3ec571bc-1760-4088-97fc-70da82e5796e",
            "userId": "b56ef446-99a1-4ade-87ae-5bae165ee7bd",
            "fileName": "Billing_Report_2024.23.04.csv",
            "status": "PENDING",
            "createdDate": "2024-04-23T16:50:58.785346+05:30"
        },
        {
            "fileId": "4bbcf5fa-2ad3-4856-8dc9-36109ad7e2f7",
            "userId": "b56ef446-99a1-4ade-87ae-5bae165ee7bd",
            "fileName": "Billing_Report_2024.23.04.csv",
            "status": "PENDING",
            "createdDate": "2024-04-23T17:05:13.315902+05:30"
        },
        {
            "fileId": "40f923ae-4a29-447a-9923-d17628891510",
            "userId": "b56ef446-99a1-4ade-87ae-5bae165ee7bd",
            "fileName": "Billing_Report_2024.23.04.csv",
            "status": "PENDING",
            "createdDate": "2024-04-23T17:21:13.545041+05:30"
        },
        {
            "fileId": "32669166-5bc7-49da-bb64-48a82a9ae43a",
            "userId": "b56ef446-99a1-4ade-87ae-5bae165ee7bd",
            "fileName": "Billing_Report_2024.23.04.csv",
            "status": "PENDING",
            "createdDate": "2024-04-23T17:33:18.063927+05:30"
        },
        {
            "fileId": "3d4916d7-36d9-43ae-b4f5-9ae3be785fcd",
            "userId": "b56ef446-99a1-4ade-87ae-5bae165ee7bd",
            "fileName": "Billing_Report_2024.23.04.csv",
            "status": "PENDING",
            "createdDate": "2024-04-23T18:11:10.779886+05:30"
        }];

export default {
  setup() {
    const pagination = ref({
      sortBy: "desc",
      descending: false,
      page: 1,
      rowsPerPage: 5,
      // rowsNumber: xx if getting data from a server
    });

    return {
      pagination,

      columns,
      rows,

      pagesNumber: computed(() => {
        return Math.ceil(rows.length / pagination.value.rowsPerPage);
      }),
    };
  },
};
</script>
<style>
.customEllipsis {
  text-overflow: ellipsis !important;
  white-space: nowrap !important;
  overflow: hidden !important;
}
</style>