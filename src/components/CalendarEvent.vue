<template>
        <div 
            class="alert text-center"
            :class = "getEventColor" 
            >


            <div>{{ event.title }} </div>
            <div>
                <i class="fa fa-edit mr-2"></i>
                <i class="fa fa-trash"></i>
            </div>
        </div>
</template>

<script>


    export default {
        name: 'CalendarEvent',
        props: ['event', 'day'],
        computed: {
            getEventColor() {
                return 'alert-'+this.event.color;
            }
        }
    }

</script>

<style>
    
</style>