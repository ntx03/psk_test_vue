<script>
import PopupString from './PopupString.vue';
export default {
    name: 'Popup',
    props: {
        popup: {
            type: Object,

        },
        float: {
            type: Object,
        },
    },
    setup(props) {
        const translateBoolian = (data) => data ? "Да" : "Нет";

        return () => {
            return (
                <div className={props.popup.value ? 'popup' : 'popup_none'}>
                    <h2 className='popup__title'>Сведения о квартире</h2>
                    <PopupString name={'Цена в рублях:'} data={`${props.float.value.cost} рублей`} />
                    <PopupString name={'Номер этажа:'} data={`${props.float.value.floor} этаж`} />
                    <PopupString name={'Номер квартиры:'} data={props.float.value.number} />
                    <PopupString name={'Тип объекта(квартира, нежилое, паркинг):'} data={props.float.value.type} />
                    <PopupString name={'Тип планировка:'} data={props.float.value.plan_type} />
                    <PopupString name={'Площадь:'} data={`${props.float.value.square} кв.м`} />
                    <PopupString name={'Текущий статус (Выданы ключи, бронь, свободна):'} data={props.float.value.status} />
                    <PopupString name={'Субсидированная:'} data={translateBoolian(props.float.value.subsidy)} />
                    <PopupString name={'Маржинальная:'} data={translateBoolian(props.float.value.marginal)} />
                    <PopupString name={'С ремонтом:'} data={translateBoolian(props.float.value.renovation)} />
                    <PopupString name={'С рассрочкой:'} data={translateBoolian(props.float.value.installment)} />
                    <button className='popup__button' onClick={() => props.popup.value = false} >Закрыть</button>
                </div>
            )
        }
    },
}
</script>
<style>
.popup {
    position: fixed;
    display: flex;
    flex-direction: column;
    z-index: 1;
    top: 5%;
    left: 40%;
    margin: 0px 0px 0px 0px;
    background-color: whitesmoke;
    border: 1px solid black;
    border-radius: 10px;
    z-index: 1;
    opacity: 1;
    visibility: visible;
    transition: 0.3s;
}

.popup_none {
    opacity: 0;
    visibility: hidden;
    transition: 0.2s;
}

.popup__title {
    font-family: 'Courier New', Courier, monospace;
    font-size: 16px;
    line-height: 22px;
    font-weight: 600;
    text-align: center;
    margin: 20px auto 0 auto;
    color: black;
}

.popup__button {
    width: 200px;
    height: 30px;
    border: none;
    background-color: green;
    color: white;
    font-family: 'Courier New', Courier, monospace;
    font-size: 12px;
    line-height: 16px;
    font-weight: 500;
    border-radius: 5px;
    margin: 10px auto 20px auto;
    transition: 0.5s;
}

.popup__button:hover {
    cursor: pointer;
    opacity: 0.8;
}
</style>