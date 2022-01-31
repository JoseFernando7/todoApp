<template>
    <div class="contenido">
        <center>
            <h1> {{ titulo }} </h1>
            <input ref="item" type="text" v-model="nuevaTarea" placeholder="Escriba su tarea a realizar">
            <button class="btnAgregar" @click="agregarElemento"> Agregar </button>
            <ul>
                <li v-for="todo in todoList" :key="todo.id">
                    {{ todo }}
                    <button class="btnEliminar" @click="eliminarElemento(todo)"> Eliminar </button>
                </li>
            </ul>
        </center>
        
    </div>
</template>


<script>
    export default 
    {
        data()
        {
            return {
                titulo: 'Lista de tareas',

                todoList: [],

                nuevaTarea: ''
            }
        },

        methods:
        {
            agregarElemento()
            {
                //Si el contenido del cuadro de texto no está vacío, agregarlo al array y mostrar en pantalla
                if (this.nuevaTarea != '') 
                {
                    this.todoList.push(this.nuevaTarea);
                }
                this.nuevaTarea = '';
                this.$refs.item.focus();
            },

            eliminarElemento(elemento)
            {
                //Almacenar el indice del elemento del array del que se pulsó el botón en la variable 'indice'
                let indice = this.todoList.indexOf(elemento);
                //Eliminar el elemento ubicado en el indice que se encontró arriba y actualizar en pantalla.
                this.todoList.splice(indice, 1);
            }
        }
    }
</script>


<style scoped>
    .contenido
    {
        font-family: Arial, Helvetica, sans-serif;
        font-size: 1.5em;
    }

    input
    {
        width: 400px;
        padding: 10px;
    }

    button
    {
        padding: 10px;
        margin-left: 10px;
        background: rgb(24, 155, 231);
        border: none;
        border-radius: 5px;
    }

    .btnAgregar:hover
    {
        background: rgb(70, 178, 240);
        cursor: pointer;
    }

    .btnEliminar:hover
    {
        background: rgb(172, 14, 9);
        color: #fff;
        cursor: pointer;
    }

    ul
    {
        border-top: 2px solid #000;
        margin: 50px;
    }

    li
    {
        list-style: none;
        display: flex;
        justify-content: space-between;
        margin: 20px 0;
        padding: 10px 0;
        border-bottom: 1px solid #000;
        margin-left: -40px;
    }
</style>