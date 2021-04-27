<template>
  <b-modal 
    id="user-modal" 
    centered 
    hide-header-close
    hide-footer
    no-close-on-backdrop
    no-close-on-esc 
    content-class="shadow"
    title="Create User" 
    v-model="show"
    class="modal"
  >
    <div class="name-section">
      <div class="form-group">
        <div class="item-header">
          <h4>Full Name</h4>
          <hr/>
        </div>
        <input
          v-model="user.full_name"
          type="text"
          class="form-control"
          id="name"
          required
        />
      </div>
    </div>

    <div class="form-group">
      <div class="item-header">
        <h4>Email</h4>
        <hr/>
      </div>
      <input
        v-model="user.email"
        type="email"
        class="form-control"
        id="email"
        required
      />
    </div>

    <div class="form-group">
      <div class="item-header">
        <h4>Birthday</h4>
        <hr/>
      </div>
      <b-form-datepicker 
        v-model="user.birthday" 
        class="mb-2"
      ></b-form-datepicker>
    </div>
    

    <div class="action-btn-container">
      <button type="button" class="cancel-btn" @click="$emit('closeModal')">Cancel</button>
      <button type="submit" class="btn save-btn" @click="$emit('addUser', user)">Create User</button>
    </div>
  </b-modal>
</template>

<script>
export default {
  props: {
    show: {
      type: Boolean,
      default: false
    }
  },
  data() {
    return {
      user: {
        full_name: '',
        email: '',
        birthday: '',
      }
    }
  }
}
</script>

<style lang="scss" scoped>

.cancel-btn, .save-btn {
  float: right;
  border: 1px solid #000000;
  background: white;
  padding: 10px 3em;
  margin: 1em .5em;
  border-radius: 10px;
}

.save-btn {
  border: unset;
  background: #37B347;
  color: white;
  padding: 10px 2em;
}

::v-deep .modal {
  background: rgba(0, 0, 0, 0.50);

  .modal-dialog {
    max-width: 700px;

    .modal-content {
      border-radius: 10px;

      .modal-header {
        border-bottom: unset;
        padding: 1em 2em;

        h5 {
          font-family: 'Source Sans Pro', sans-serif;
          font-weight: 600;
          font-size: 20pt;
          color: #0A0A0A;
        }

        .close {
          font-size: 30pt;
        }
      }

      .modal-body {
        padding: 0 2em;

        .item-header {
          display: flex;
          flex-direction: row;
          align-items: center;
          justify-content: space-between;
          margin: .5em 0;
      
          h4 {
            margin-bottom: 0;
            font-size: 11pt;
            color: #57585B;
            font-family: 'Source Sans Pro', sans-serif;
            font-weight: bold;
            font-size: 12pt;
          }
      
          hr {
            width: 85%;
            border-top: 2px solid rgba(0,0,0,.1);
      
            @media only screen and (max-width: 600px) {
              width: 50%;
            }
          }
        }

        .form-control {
          border-radius: 10px;
        }

        .action-btn-container {
          display: flex;
          flex-direction: row;
          align-items: center;
          justify-content: flex-end;
          margin-top: 2em;
        }
      }
    }
  }
}
</style>