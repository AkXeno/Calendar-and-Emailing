<template>
    <div class="container">
        <form>
            <input type="text" v-model="eventName" placeholder="Enter text" />
            <p>Event Name: {{ eventName }}</p>
        </form>
    </div>
    <FullCalendar v-bind:options="options" />
</template>

<script>
    export default {
        data() {
            return {
                eventName: '',
            }
        },
    }
</script>

<script setup>
    import { ref, reactive } from 'vue'
    import '@fullcalendar/core/vdom'
    import FullCalendar from '@fullcalendar/vue3'
    import DayGridPlugin from '@fullcalendar/daygrid'
    import TimeGridPlugin from '@fullcalendar/timegrid'
    import InteractionPlugin from '@fullcalendar/interaction'
    import ListPlugin from '@fullcalendar/list'

    const eventName = ref('')

    const options = reactive({
        plugins: [DayGridPlugin, TimeGridPlugin, InteractionPlugin, ListPlugin],
        initialView: 'dayGridMonth',
        headerToolbar: {
            left: 'prev today next',
            center: 'title',
            right: 'listDay timeGridDay dayGridWeek dayGridMonth',
        },
        footerToolbar: {
            left: 'custom1',
            center: '',
            right: 'prev next'
        },
        customButtons: {
            custom1: {
                text: 'Request Extension',
                click: function() {
                    alert('here');
                }
            }
        },
        editable: true,
        selectable: true,
        weekends: true,
        select: (arg) => {
            const cal = arg.view.calendar
            cal.unselect()
            cal.addEvent({
                id: `${eventName.value}`,
                title: `${eventName.value}`, //id.value
                start: arg.start,
                end: arg.end,
                allDay: true
            })
        },
        eventClick: (arg) => {
            alert(arg.event.title)
        }
    })

    // export default {
    //     components: {
    //         FullCalendar
    //     },
    //     data(){
    //         return {
    //             calendarOptions: {
    //                 plugins: [DayGridPlugin, TimeGridPlugin, InteractionPlugin, ListPlugin],
    //                 initialView: 'dayGridMonth',

    //                 weekends: false
    //             }
    //         }
    //     },
    //     methods: {
    //         toggleWeekends: function() {
    //         this.calendarOptions.weekends = !this.calendarOptions.weekends
    //         }
    //     }
    // }

</script>

<style>
.container {
  display: block;
  margin:auto;
  text-align: center;
  border-radius: 5px;
  background-color: #28323b;
  padding: 20px;
  width: 20%;
}

input[type=text] {
  width: 100%;
  padding: 12px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
  margin-top: 6px;
  margin-bottom: 6px;
  resize: vertical;
}
</style>