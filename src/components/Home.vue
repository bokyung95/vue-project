<template>
    <div>
        <div>
            <div v-if="exsitsName">
                <!-- <h1 @click="sayHello">Home</h1> -->
                <input type="text" v-model="userName" @keyup.enter="enterName" placeholder="이름을 입력해주세요.">
                <button @click="enterName">입력</button>
            </div>
            <div v-else>
                {{ user[0].name }} 님 환영합니다.
            </div>
        </div >
        <div v-if="!exsitsName">
            <!-- <TodoInput /> -->
            <div class="add_todo_input_area">
                <input 
                    v-model="todoText"
                    type="text" 
                    class="todo_input" 
                    placeholder="type todo" 
                    @keyup.enter="addTodoItem"
                />
                <button class="add_todo_button" @click="addTodoItem">Add</button>
            </div>
            <div class="list_area">
                <ul class="list">
                    <TodoList 
                        v-for="todo in todos" 
                        :key="todo.item"
                        :todo="todo"
                        @toggle-checkbox="toggleCheckbox"
                        @click-delete = "deleteTodo"
                    />
                </ul>
            </div>
        </div>
    </div>
</template>

<script>
// import TodoInput from '@/components/todoList/TodoInput';
import TodoList from '@/components/todoList/TodoList';

export default {
    components : {
        // TodoInput,
        TodoList
    },
    data() {
        return {
            userName : '',
            user : [''],
            exsitsName : true,
            // todo list data
            todos: [],
            todoText : ''
        }
    },
    methods : {
        // sayHello() {
        //     console.log('say Hello')
        // }
        enterName(event) {
            if (this.userName !== "") {
                let obj = {name : this.userName};
                //로컬스토리지에 넣기 위해 문자열로 변환
                localStorage.setItem(this.userName, JSON.stringify(obj));
                this.clearInput();
                this.exsitsName = false;
                if (localStorage.length > 0 ) {
                    this.user.splice(0);
                    this.user.push(JSON.parse(localStorage.getItem(localStorage.key(0))));
                    this.exsitsName = false;
                }
            }
        },
        clearInput() {
            this.userName = '';
        },
        addTodoItem(e) {
            // console.log(e.target.value);
            this.todos.push({
                item : e.target.value,
                completed : false
            });
            this.todoText = '';
        },
        toggleCheckbox({item, checked}) {
            // console.log(item, checked);
            const index = this.todos.findIndex(function(todo) {
                return todo.item === item
            });
            this.todos[index].completed = checked;
        },
        deleteTodo(item) {
            const index = this.todos.findIndex(todo => {
                return todo.item === item
            });
            this.todos.splice(index, 1);
            // this.todos = this.todos.filter(todo => todo.item !== item);
        }
    },
    created() {
        if (localStorage.length > 0 ) {
            this.user.splice(0);
            this.user.push(JSON.parse(localStorage.getItem(localStorage.key(0))));
            // console.log(this.user);
            this.exsitsName = false;
        }else {
            this.exsitsName = true;
        }
    }
}
</script>
