<script>
export default {
    name: 'PopupString',
    props: {
        name: {
            type: String,
            required: true
        },
        data: {
            type: String,

        },
    },
    setup(props) {

        return () => {
            return (
                <div className='popup__text-container'>
                    <p className='popup__text_bold'>{props.name}</p>
                    <p className='popup__text'>{props.data}</p>
                </div>
            )
        }
    },
}
</script>

<style>
.popup__text-container {
    display: flex;
    gap: 10px;
    margin: 10px 20px 0px 20px;
}

.popup__text_bold {
    font-family: 'Courier New', Courier, monospace;
    font-size: 12px;
    line-height: 16px;
    font-weight: 600;
    width: 170px;
    margin: 0;
    text-align: end;
}

.popup__text {
    font-family: 'Courier New', Courier, monospace;
    font-size: 12px;
    line-height: 16px;
    font-weight: 400;
    margin: 0;
}
</style>