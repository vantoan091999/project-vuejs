<template>
   <div id="exampleModalLive" class="modal fade show" @click.self="onCloseModal"
    tabindex="-1" role="dialog" aria-labelledby="exampleModalLiveLabel" style="padding-right: 17px; display: block;">
    <div class="modal-dialog" role="document">
      <div class="modal-content" :class="{'bg-purple': themme === 'contact'}">
        <div class="modal-header">
          <h5 class="modal-title" id="exampleModalLiveLabel">{{ title }}</h5>
          <button type="button" class="close" data-dismiss="modal" aria-label="Close">
           
          </button>
        </div>
        <div class="modal-header">
          <h5 class="modal-title" id="exampleModalLiveLabel">
            <slot name="header"></slot>
          </h5>
         
        </div>
        <div class="modal-body">
          <!-- <p>{{ content }}</p> -->
          <slot />
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-secondary" @click.self="onCloseModal"
           data-dismiss="modal">Close</button>
          <button type="button" class="btn btn-primary">Save changes</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  
  export default {
    props: {
      title: {
        type: String,
        required: true
      },
      content: {
        title: String,
        default: ""
      },
       themme: {
        title: String,
        default: "example",
        validator(value) {
          return ["example", "sales", "contact"].includes(value)
        }
      }
    },
    data() {
      return {
        // title: "Modal title"
      }
    },
    methods: {
      onCloseModal (){
        this.$emit("close");
      }
    }
  }
</script>

<style  lang="css">
    .fade.show {
      opacity: 1;
    }
    .modal {
    z-index: 1072;
}
.modal {
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    z-index: 1050;
    display: block;
    overflow: hidden;
    outline: 0;
    background-color: rgba(0,0,0,.2);
}

.fade {
    opacity: 0;
    transition: opacity .15s linear;
}
.modal-dialog {
    max-width: 500px;
    margin: 1.75rem auto;
}
.modal-dialog {
    position: relative;
    width: auto;
    margin: 0.5rem;
    pointer-events: none;
}
.modal-content {
    position: relative;
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-orient: vertical;
    -webkit-box-direction: normal;
    -ms-flex-direction: column;
    flex-direction: column;
    width: 100%;
    pointer-events: auto;
    background-color: #fff;
    background-clip: padding-box;
    border: 1px solid rgba(0,0,0,.2);
    border-radius: 0.3rem;
    outline: 0;
}
.modal-content .bg-purple {
  background-color: aqua;
}
.modal-header {
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-align: start;
    -ms-flex-align: start;
    align-items: flex-start;
    -webkit-box-pack: justify;
    -ms-flex-pack: justify;
    justify-content: space-between;
    padding: 1rem;
    border-bottom: 1px solid #e9ecef;
    border-top-left-radius: 0.3rem;
    border-top-right-radius: 0.3rem;
}
.modal-title {
    margin-bottom: 0;
    line-height: 1.5;
}
.modal-body {
    position: relative;
    -webkit-box-flex: 1;
    -ms-flex: 1 1 auto;
    flex: 1 1 auto;
    padding: 1rem;
}
.modal-footer {
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-align: center;
    -ms-flex-align: center;
    align-items: center;
    -webkit-box-pack: end;
    -ms-flex-pack: end;
    justify-content: flex-end;
    padding: 1rem;
    border-top: 1px solid #e9ecef;
}
</style>