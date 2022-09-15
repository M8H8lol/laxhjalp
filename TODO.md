- [ ] Visa en lista på folk som kan erbjuda läxhjälp
    - [X] Skapa fejkad data för X antal läxhjälpare
    - [ ] Skapa en komponent i Vue som kan rita upp listan
        - [ ] Fixa så att ämnen och nivåer visas korrekt
- [ ] Vi behöver ett interface för att kunna filterera i listan
    - [ ] Checkboxes för ämnen?
    

<ul>
    <li v-for="greeting in greetings">
        {{greeting.lang}}: {{greeting.text}}
    </li>
</ul>

<script>
    export default {
        data() {
            return {
                greetings: [
                    {
                        text: "Hej",
                        lang: "se"
                    },
                    {
                        text: "Hello",
                        lang: "en"
                    },
                    {
                        text: "Hola",
                        lang: "es"
                    },
                ]
            }
        }
    }
</script>