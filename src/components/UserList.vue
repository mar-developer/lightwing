<template>
  <div class="users-table">
    <div class="table-header">
      <b-button class="add-btn" @click="modal.show = true">Add User</b-button>
    </div>

    <b-table 
      id="students-table"
      show-empty
      responsive
      sticky-header
      no-border-collapse
      :items="items"
      :busy="!items"
      :fields="fields"
    >
      <template #table-busy>
        <div class="text-center text-success my-2">
          <b-spinner class="align-middle"></b-spinner>
          <strong>Loading...</strong>
        </div>
      </template>
    </b-table>

    <AddUserModal 
      :show="modal.show"
      @closeModal="modal.show = false"
      @addUser="addUser"
    /> 
  </div>
</template>

<script>
export default {
  components: {
    AddUserModal: () => import('@/components/AddUser.vue')
  },
  data() {
    return {
      sortBy: 'name',
      sortDesc: false,
      sortDirection: 'asc',
      fields: [
        { key: 'id', label: 'ID', sortable: true, class: 'id-max-width' },
        { key: 'full_name', label: 'Name', sortable: true, class: 'name-max-width' },
        { key: 'email', label: 'Email', sortable: true, class: 'email-max-width' },
        { key: 'birthday', label: 'Date of Birth', sortable: true, class: 'birthday-max-width' }
      ],
      modal: {
        show: false
      },
      items: [{
        "id": 1,
        "full_name": "Perren Ilyuchyov",
        "email": "pilyuchyov0@yahoo.co.jp",
        "birthday": "1998-01-31"
      }, {
        "id": 2,
        "full_name": "Allie Pinnigar",
        "email": "apinnigar1@unicef.org",
        "birthday": "1998-03-17"
      }, {
        "id": 3,
        "full_name": "Timmie Dent",
        "email": "tdent2@vimeo.com",
        "birthday": "1996-09-04"
      }, {
        "id": 4,
        "full_name": "Valerie Kropp",
        "email": "vkropp3@who.int",
        "birthday": "1997-09-10"
      }, {
        "id": 5,
        "full_name": "Bari Scrinage",
        "email": "bscrinage4@macromedia.com",
        "birthday": "1996-06-02"
      }, {
        "id": 6,
        "full_name": "Vachel Kelleway",
        "email": "vkelleway5@friendfeed.com",
        "birthday": "1998-02-25"
      }]
    }
  },
  methods: {
    addUser(data) {
      const userCount = this.items.length

      Object.assign(data, {id: userCount+1})
      this.items.push(data)
      this.modal.show = false
    }
  }
}
</script>
<style lang="scss" scoped>
  .users-table {
    border-radius: 10px;
    background-color: white;
    box-shadow: 0px 1px 7px rgba(0, 0, 0, 0.25);
    height: 100%;

    .table-header {
      display: flex;
      flex-direction: row;
      justify-content: flex-end;
      align-items: center;

      .filter {
        width: 500px;
        margin: 1em 2em;

        .search-btn {
          color: white;
          background-color: #043D10;
        }
      }

      .add-btn {
        color: white;
        background-color: #043D10;
        margin: 1em 2em;
        padding: 5px 2em;
        border-radius: 30px;
      }
    }

    ::v-deep .b-table-sticky-header {
      min-height: 450px;

      .table {
        margin-top: 0;
        padding: 0 2em;
        background-color: white;
  
        .name-max-width {
          width: 300px;
        }
  
        .id-max-width {
          width: 100px;
        }
        .email-max-width {
          width: 400px;
        }
        .birthday-max-width {
          width: 300px;
        }
      }
    }

    ::v-deep .table-pagination {
      padding: 1em 0;

      .page-item .page-link {
        color: #043D10;

        &:focus {
          box-shadow: 0 0 0 0.25rem rgba(4, 61, 16, 0.25) !important;
        }
      }

      .page-item.active .page-link {
        color: white;
        border: unset;
        background-color: #043D10 !important;

        &:focus {
          box-shadow: 0 0 0 0.25rem rgba(4, 61, 16, 0.25) !important;
        }
      }
    }
  }
</style>