<script>
    let people = [
        {name: 'joe', age: '24'},
        {name: 'mike', age: '36'},
        {name: 'david', age: '32'},
    ]

    people.sort((a,b) => b.age - a.age)


    let person = {name: null, age: null};

    function addPerson(event) {
        people = [...people, person]
        person = {name: null, age: null};

        people.sort((a,b) => b.age - a.age)
    }

    function isOld(age) {
        if(age < 25) {
            return 'aint that old'
        }
        else if(age < 30) {
            return 'still got it'
        }
        else {
            return 'you is old'
        }
    }

</script>

<div>
    <input bind:value={person.name} type="text">
    <input bind:value={person.age} type="text">
    <button disabled={!(person.age && person.name)} on:click={addPerson}>submit</button>
</div>

<div style="margin-top: 10px;"></div>
<div>
    <table>
        <thead>
            <th>name</th>
            <th>age</th>
            <th>old?</th>
        </thead>
        <tbody>
        {#each people as person}
        <tr>
            <td>{person.name}</td>
            <td>{person.age}</td>
            <td>{isOld(person.age)}</td>
        </tr>        
        {/each}
        </tbody>
    </table>
</div>




<style>
    p {
        color: red;
    }    
    div {
        display: inline-block;
    }
    td {
        padding: 10px
    }
</style>
