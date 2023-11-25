<template>
    <div class="note">
        <div class="details">
            <p class="title">{{ note.title }}</p>
            <span class="body">{{ note.body }}</span>
        </div>
        <div class="bottom-content">
            <span>{{ new Date(note.date).toLocaleDateString('en-us', { day: "numeric", year: "numeric", month: "long" })
            }}</span>
            <div class="settings">
                <i class="uil uil-ellipsis-h"></i>
                <ul class="menu">
                    <li @click="$emit('edit', note)"><i class="uil uil-pen"></i>Edit</li>
                    <li @click="$emit('remove', note)"><i class="uil uil-trash"></i>Delete</li>
                </ul>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        note: {
            type: Object,
            require: true,
        }
    },
}
</script>

<style scoped>
.note {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    width: 100%;
    overflow-y: scroll;
}

.note::-webkit-scrollbar {
    width: 5px;
}

.note::-webkit-scrollbar-track {
    background: none;
}

.note::-webkit-scrollbar-thumb {
    background-color: rgba(0, 0, 0, 0.25);
    border-radius: 3px;
}

.note p {
    font-style: 22px;
    font-weight: 500;
}

.note span {
    display: block;
    margin-top: 5px;
    color: #575757;
    font-style: 16px;
}

.note .bottom-content {
    padding-top: 10px;
    border-top: 1px solid #ccc;
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.bottom-content span {
    color: #6d6d6d;
    font-style: 14px;
}

.bottom-content .settings i {
    color: #6d6d6d;
    font-style: 15px;
    cursor: pointer;
}

.settings {
    position: relative;
}

.settings .menu {
    position: absolute;
    bottom: 0;
    padding: 5px 0;
    background: #fff;
    border-radius: 4px;
    transform: scale(0);
    transform-origin: top left;
    box-shadow: 0 0 6px rgba(0, 0, 0, 0.15);
    transition: transform 0.2s ease;
}

.settings:hover .menu {
    transform: scale(1);
}

.settings .menu li {
    height: 25px;
    font-style: 16px;
    cursor: pointer;
    border-radius: 0;
    padding: 17px 15px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    justify-content: flex-start;
}

.menu li:hover {
    background: #f5f5f5;
}

.menu li i {
    padding-right: 8px;
}
</style>