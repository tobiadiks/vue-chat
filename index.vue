<html>

<head>
    <script src="./js/@vue2.js"></script>
    <script src="./js/tailwindcss.js"></script>
</head>


<div class="min-h-screen w-full" id="app">
    <nav-bar></nav-bar>
    <!-- body -->
    <div class="h-full flex w-full">
        <chat-list-container>
            <!-- logged in user card -->
            <user-card name="Ajitu Naomi" role="Product Manager"></user-card>
            <!-- search -->
            <input placeholder="Search" class="bg-white border text-sm focus:outline:none rounded-lg mt-4 w-full p-1" />

            <div class="mt-4 grid grid-cols-1">
                <!-- chat card -->
                <chat-card name="Phil Jones" last_date="12:30 PM" last_message="Hello World" unread="2"></chat-card>
                <chat-card name="James Brown" last_date="12:30 PM" last_message="Good morning" unread="9"></chat-card>
            </div>
        </chat-list-container>
        <chat-container current_chat="Phil Jones">
            <!-- messages -->
        <outgoing text="Lorem ipsum dolor sit amet consectetur"></outgoing>
        <incoming text="sit amet consectetur adipisicing elit. Voluptatibus ut ipsa blanditiis, sint suscipit sit illo dicta assumenda deleniti animi aspernatur sapiente illum recusandae aperiam laborum eaque. Nesciunt, consectetur debitis."></incoming>
        <outgoing text="Lorem ipsum dolor sit amet consectetur"></outgoing>
        <incoming text="sit amet consectetur adipisicing elit. Voluptatibus ut ipsa blanditiis, sint suscipit sit illo dicta assumenda deleniti animi aspernatur sapiente illum recusandae aperiam laborum eaque. Nesciunt, consectetur debitis."></incoming>
        <outgoing text="Lorem ipsum dolor sit amet consectetur"></outgoing>
        <incoming text="sit amet consectetur adipisicing elit. Voluptatibus ut ipsa blanditiis, sint suscipit sit illo dicta assumenda deleniti animi aspernatur sapiente illum recusandae aperiam laborum eaque. Nesciunt, consectetur debitis."></incoming>
        </chat-container>

    </div>

</div>
</div>



<script>
    Vue.component('outgoing', {
        props: {
            text:String
        },
        template: `
        <div class="bg-red-500 p-2 rounded-l-md w-1/2 text-white text-end self-end">
{{text}}
    </div>
    `
    })

    Vue.component('incoming', {
        props: {
            text:String
        },
        template: `
        <div class="bg-gray-200 p-2 rounded-r-md w-1/2 text-black ">
                {{text}}
            </div>
    `
    })

Vue.component('chat-container', {
        props: {
            current_chat:String
        },
        template: `
        <div class="w-3/4  py-4  space-y-4 border-r flex flex-col    bg-white ">
            <div class="w-full py-2 px-4 border-b mb-0  h-1/8 font-bold">
                {{current_chat}}
            </div>

            <div class="w-full pl-4 py-4 pr-4 space-y-4 flex flex-col h-6/8 overflow-y-scroll bg-white">
            <slot/>
            </div>

            <form class="w-full py-4 h-1/8 px-4 border-t mb-4 flex  font-bold">
                <input placeholder="Write Something" class="bg-gray-200 text-sm focus:outline:none rounded-lg  w-full px-4 py-2" />
                <button class='bg-red-500 text-white font-bold ml-2 px-4 py-2 text-center rounded-lg'>Send</button>
            </form>

    </div>

    `
    })

    Vue.component('chat-card', {
        props: {
            last_date: String, last_message: String, name: String, unread: String
        },
        template: `
    <div class="w-full cursor-pointer p-2 hover:bg-white">
            <div class="flex justify-between">
                <div class="text-red-500 my-auto ">{{name}}</div>
                <div class="text-sm text-gray-500 my-auto">{{last_date}}</div>
            </div>
            
            <div class="flex justify-between mt-1">
                <div class="text-sm text-gray-500 my-auto">{{last_message?.length>8?last_message.slice(0,8)+'...':last_message}}</div>
                <div class=" bg-red-500 p-1 text-xs h-6 w-6 text-center text-white rounded-full ">{{unread}}</div>
                
            </div>
         </div>
    `
    })

    Vue.component('user-card', {
        props: {
            name: String,
            role: String
        },
        template: `
<div class="w-full rounded-sm">
        <div class="font-bold text-red-500 ">{{name}}</div>
        <div class="text-sm text-gray-500">{{role}}</div>
     </div>
    `
    })

    Vue.component('chat-list-container', {

        template: `
<div class="w-1/4 pl-4 pr-2 py-4  border-r max-h-screen ovrerflow-y-scroll  h-full bg-gray-100">
    <slot/>
</div>
    `
    })

    Vue.component('nav-bar', {
        data() {
            return {
                // message: 'hi'
            }
        },
        template: `
    <div class="bg-red-500 p-4 flex w-full  ">
    <div class='text-white self-end w-fit'>Chat</div></div>
        `
    })

    let app = new Vue({ el: '#app' })


</script>




</html>