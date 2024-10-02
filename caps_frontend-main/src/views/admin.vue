<template>
    <div id="app">
      <Menu />
    </div>
  
    <div class="container">
      <div class="flex-container">
        <div class="right-container">
          <!-- Display messages as pop-ups -->
          <transition-group name="fade" mode="out-in">
            <div v-for="message in messages" :key="message.id" class="popup">
              {{ message.text }}
            </div>
          </transition-group>
        </div>
        <SchedulerComponent
        class="left-container"
        :events="events"
        :filterDate="selectedDate" 
        @event-updated="logEventUpdate"
      ></SchedulerComponent>
      </div>
    </div>
  </template>
  
  <script>
  import SchedulerComponent from '../components/admin/SchedulerComponent.vue'
  import Menu from '../components/admin/Menu.vue'
  
  export default {
    name: "app",
    components: {
      SchedulerComponent,
      Menu,
    },
    data() {
      return {
        events: [
          {
            id: 1,
            start_date: "2020-01-20 6:00",
            end_date: "2020-01-20 15:00",
            text: "Event 1",
          },
          {
            id: 2,
            start_date: "2020-01-23 6:00",
            end_date: "2020-01-23 20:00",
            text: "Event 2",
          },
        ],
        messages: [],
        selectedDate: null,
      };
    },
    methods: {
      addMessage(message) {
        this.messages.unshift(message);
        if (this.messages.length > 40) {
          this.messages.pop();
        }
      },
  
      logEventUpdate(id, mode, ev) {
        let text = ev && ev.text ? ` (${ev.text})` : "";
        let message = { id: Date.now(), text: `Event ${mode}: ${id} ${text}` };
        this.addMessage(message);
  
        // Remove the message after 2 seconds
        setTimeout(() => {
          this.messages = this.messages.filter((msg) => msg.id !== message.id);
        }, 2000);
      },
      handleDateSelection(date) {
      this.selectedDate = date; // Update the selected date
    },
    },
  };
  </script>
  
  <style>
  html,
  body {
    height: 100%;
    margin: 0;
    padding: 0;
  }
  
  .container {
    height: 100%;
    width: 100%;
  }
  
  .flex-container {
    display: flex;
  }
  
  .left-container {
    overflow: hidden;
    position: relative;
    height: 99vh;
    display: inline-block;
    width: 80%;
  }
  
  .right-container {
    border-right: 1px solid #cecece;
    float: right;
    height: 100%;
    width: 19%;
    position: relative;
    z-index: 2;
  }
  
  .scheduler-messages {
    list-style-type: none;
    height: 50%;
    margin: 0;
    overflow-x: hidden;
    overflow-y: auto;
    padding-left: 5px;
  }
  
  .scheduler-messages > .scheduler-message {
    background-color: #f4f4f4;
    box-shadow: inset 5px 0 #d69000;
    font-family: Geneva, Arial, Helvetica, sans-serif;
    font-size: 14px;
    margin: 5px 0;
    padding: 8px 0 8px 10px;
  }
  
  .popup {
    position: fixed;
    top: 10px;
    right: 10px;
    background-color: #f4f4f4;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
    padding: 10px;
    border-radius: 5px;
    animation: fadeOut 2s forwards;
  }
  
  @keyframes fadeOut {
    from {
      opacity: 1;
    }
    to {
      opacity: 1;
    }
  }
  </style>
  