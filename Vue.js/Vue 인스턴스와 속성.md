## Vue 인스턴스
- 라이프사이클 : 생성, 부착, 변경, 소멸
- beforeCreate() created() beforeMount() mounted() beforeUpdate() updated() beforeDestroy() destroyed()

## Vue 속성
```javascript
new Vue({
    el: '#app',
    data: {
        message: '',
        count: 0,
        member; {},
        members: [],
    },
    // ES5
    data: function() {
        return {
            ...
        }
    },
    data() {
        return {
            ...
        }
    },
    methods: {
        doA() : {
        }
    },
    filters: {
        priceUnit(value) {
            return `${value} 만원`; // 지역필터선언 => {{ data-name | price | priceUnit }}
        }
    },
    template: {
    },
    components: {
    },
    router: {
    },
});
```
