<template>
    
    <li class="list_item">
        {{todo.completed}}
        <input 
            type="checkbox" 
            :check="todo.completed" 
            class="list_item_checkbox"
            @change="toggleCheckbox"
        />
        <label :for="todo.item" class="list_label">
            <span 
                class="list_text" 
                :style="todo.completed ? 'text-decoration : line-through; color : gray' : ''"
            >
                    {{todo.item}}
            </span>
        </label>
        <button class="list_delete_btn" @click="clickDelete">Delete</button>
    </li>
        
</template>

<script>
export default {
    props: {
        todo: {
            type: Object,
            required : true
        }
    },
    methods:{
        toggleCheckbox(e){
            this.$emit('toggle-checkbox',{
                item: this.todo.item,
                checked: e.target.checked
            })
        },
        clickDelete() {
            this.$emit('click-delete',this.todo.item);
        }
    }
}
</script>