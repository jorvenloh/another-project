<template>
  <v-data-table
    :headers="headers"
    :items="tickets"
    :items-per-page="5"
    class="elevation-1"
  >
    <template v-slot:top>
      <div class="ticket__header">
        <h5>All Tickets</h5>
      </div>
    </template>
    <template v-slot:item="{ item }">
      <tr class="v-data-table-row">
        <td>
          <v-avatar color="secondary" size="44" class="mr-3">
            <v-img
              lazy-src="https://picsum.photos/id/11/10/6"
              max-height="44"
              max-width="44"
              :src="item.avatar"
            ></v-img>
          </v-avatar>
          <div class="ticket__title">
            <span>{{ item.title }}</span>
            <small>{{ item.date | dateDifference }}</small>
          </div>
        </td>
        <td>
          <div class="ticket__customer_name">
            <span>{{ item.name }}</span>
            <small>{{ item.date | onDate }}</small>
          </div>
        </td>
        <td>
          <div class="ticket__customer_date">
            <span>{{ item.date | date }}</span>
            <small>{{ item.date | time }}</small>
          </div>
        </td>
        <td>
          <span
            class="ticket__priority"
            :class="`ticket__priority__` + `${item.priority}`"
            >{{ item.priority }}</span
          >
        </td>
      </tr>
    </template>
  </v-data-table>
</template>

<script>
import moment from "moment/moment";
import ticketData from "../constants/data";
export default {
  name: "DataTable",
  filters: {
    date(date) {
      return moment(date).format("MMMM DD, YYYY");
    },
    time(date) {
      return moment(date).format("h:mm a");
    },
    onDate(date) {
      return "on " + moment(date).format("DD.MM.YYYY");
    },
    dateDifference(date) {
      return moment(date).fromNow();
    },
  },
  data: () => ({
    headers: [
      {
        text: "Ticket details",
        align: "start",
        sortable: false,
        value: "title",
      },
      { text: "Customer name", value: "name" },
      { text: "Date", value: "date" },
      { text: "Priority", value: "priority" },
    ],
    tickets: ticketData,
  }),
};
</script>

<style scoped>
.v-data-table-row {
  height: 92px;
}

.v-data-table-row span{
  font-size: 14px;
  line-height: 20px;
  font-weight: 600;
}

.v-data-table-row small {
  font-size: 12px;
  line-height: 16px;
  font-weight: 400;
}

.ticket__title {
  display: inline-block;
  position: relative;  
}

.ticket__title small,
.ticket__customer_name small,
.ticket__customer_date small {
  display: block;
  color: #c5c7cd;
}

.ticket__priority {
  color: white;
  height: 24px;
  border-radius: 1em;
  padding: 5px 12px;
  text-transform: uppercase;
  font-size: 11px !important;
  font-weight: 700;
  line-height: 13.81px;
}

.ticket__priority__high {
  background-color: #f12b2c;
}

.ticket__priority__low {
  background-color: #fec400;
}

.ticket__priority__normal {
  background-color: #29cc97;
}

.ticket__header {
  padding: 32px;
  font-size: 19px;
  line-height: 24px;
}
</style>