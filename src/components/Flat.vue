<script >
import { ref } from "vue";
import data from '../utils/data.json';

export default {
    name: 'Flat',
    props: {
        flat: {
            type: Object,
            required: true
        }
    },
    setup(props) {
        const dataFlat = data.flats[props.flat.id];
        const marker = ref(false);

        if (dataFlat.subsidy || dataFlat.marginal || dataFlat.renovation || dataFlat.renovation === true) {
            marker.value = true;
        } else marker.value = false;

        const flatStatus = () => {
            if (dataFlat.status === 'Договор') {
                return 'flat flat__yellow';
            } else if (dataFlat.status === 'Выданы ключи') {
                return 'flat flat__sold';
            } else if (dataFlat.status === 'Оформление') {
                return 'flat flat__yellow';
            } else if (dataFlat.status === 'Бронь') {
                return 'flat flat__yellow';
            } else return 'flat';
        };

        return () => {
            return (
                <div className={flatStatus()}>
                    <p className='flat__type'>{dataFlat.plan_type}</p>
                    <div className={marker.value ? 'flat__marker' : 'flat__marker_none'}></div>
                </div>
            )
        }
    },
}
</script>

<style>
.flat {
    width: 20px;
    height: 20px;
    background-color: rgba(5, 165, 5, 0.685);
    margin: 0;
    padding: 0;
    transition: 0.2s all ease;
    position: relative;
    overflow: hidden;
}

.flat__sold {
    background-color: rgb(172, 172, 172);
}

.flat__yellow {
    background-color: rgb(188, 185, 7);
}

.flat:hover {
    cursor: pointer;
    transform: scale(1.1);
}

.flat__type {
    padding: 0;
    margin: 0;
    color: #ffffff;
    font-size: 12px;
    line-height: 16px;
    padding-top: 2px;
    box-sizing: border-box;
    text-align: center;
    z-index: 1;
}

.flat__marker {
    position: absolute;
    top: -2.5px;
    right: -5px;
    transform: rotate(45deg);
    width: 10px;
    height: 7px;
    /* z-index: 1; */
    background-color: red;
}

.flat__marker_none {
    display: none;
}
</style>