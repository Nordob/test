<template>
    <div>
        <input type="text" id="suggest">
    </div>
</template> 

<script>

export default{
    mounted(){
        window.ymaps.ready(()=>{
            new window.ymaps.SuggestView('suggest')
        })
        
    }
}
</script>

<style></style>