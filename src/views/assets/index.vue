<template>
<div>
    <div class="a">
        <h2>Assets</h2>
    </div>
    <div class="box header">
        <div><input type="checkbox" v-model="statusAll" true-value="yes" false-value="no" name="checkbox-1" v-on:change="clickTout">
            Tout sélectioner
        </div>
        <div class="box absolute">
            <p>limit: </p>
            <input type="text"  placeholder="limit">
        </div>
    </div>
    <div v-for="item in allData" :key="item.id" class="box">
        <div><input type="checkbox" true-value="yes" false-value="no" v-model="item.checkBox" v-on:change="checkAllBox">
        </div>
        <div class="card">
            <p>{{ item.name}}</p>
            <p>{{ item.location}}</p>
        </div>

        <div class="absolute"></div>
    </div>
</div>
</template>

<script>
// import Login from '../components/Login.vue';
export default {
    name: "assets",
    data() {
        return {
            statusAll: 'not_accepted',
            allData: [{
                    id: 1,
                    checkBox: 'not_accepted',
                    name: 'Vu Thua Vu',
                    location: 'Ngõ 43, Cau Giay District, Hanoï, 170, Viêt Nam'
                },
                {
                    id: 2,
                    checkBox: 'not_accepted',
                    name: 'Vu Thua Vu',
                    location: 'Ngõ 43, Cau Giay District, Hanoï, 170, Viêt Nam'
                },
                {
                    id: 3,
                    checkBox: 'not_accepted',
                    name: 'Vu Thua Vu',
                    location: 'Ngõ 43, Cau Giay District, Hanoï, 170, Viêt Nam'
                },
            ]
        };
    },
    mounted() {
        // console.log('sdv')
    },
    beforeUpdate() {

        // console.log(this.statusAll)
    },
    methods: {
        clickTout() {
            console.log(this.statusAll)
            this.allData = this.allData.map(el => {
                let _el = el;
                _el.checkBox = this.statusAll;
                return _el
            })

            // console.log(this.allData)
        },

        checkAllBox() {
            let count = 0
            this.allData.forEach(el => {
                if (el.checkBox === 'no') {
                    count = ++count
                }
            })
            if (count === 0 && this.statusAll != 'yes') {
                this.statusAll = 'yes'
            }
            if (count === this.allData.length && this.statusAll != 'no') {
                this.statusAll = 'no'
            }
        }
    }
}
</script>

<style scoped>
.a {
    text-align: center;
}

.content {
    height: 900px;
    border-right: 1px solid black;
}

.note-content {
    margin: 20px;
}

.name {
    width: 180px;
    margin-top: 10px;
}

.box {
    display: flex;
    flex-wrap: nowrap;
    margin-top: 10px;
}

.dropdown-data {
    width: 120px;
}

.phone-number {
    margin-top: 20px;
}

.style-input {
    width: 60px;
    height: 40px;
}

.absolute {
    position: absolute;
    right: 0;
    /* color:; */
}

.card {
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    transition: 0.3s;
    margin-left: 60px;
    margin-right: 20px;
    width: 100%;
    padding: 12px 16px;
}

.card:hover {
    box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2);
}

</style>
