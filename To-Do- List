<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Document</title>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" rel="stylesheet"
    integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous" />
</head>

<body>
  <div class="container-fluid bg-light" style="height: 100vh; width: 100%">
    <div class="row">
      <div class="col d-flex justify-content-center">
        <h1 class="text-primary">TO-DO List</h1>
      </div>
    </div>
    <div class="row m-5">
      <div class="col-md-5">
        <input type="text" id="msg" placeholder="Enter yr msg" value="" . />
        <button id="submit" class="btn btn-primary">ADD</button>
      </div>
    </div>
    <hr />
    <div class="row">
      <div class="col d-flex justify-content-between">
        <div>
          <h5>Total count:<b><span id="count">0</span> </b></h5>
        </div>
        <div>
          <buttton class="btn btn-danger" id="clear">CLEARALL</buttton>
        </div>
      </div>
    </div>
    <hr />
    <div class="row d-flex m-3" id="body"></div>
  </div>

  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/js/bootstrap.bundle.min.js"
    integrity="sha384-MrcW6ZMFYlzcLA8Nl+NtUVF0sA7MsXsP1UyJoMp4YLEuNSfAP+JcXn/tWtIaxVXM"
    crossorigin="anonymous"></script>
  <script>
    let submit = document.getElementById("submit");
    let clear = document.getElementById('clear');
    let msg = document.getElementById("msg");
    //globalArr
    let gArr = [];
    //edit varible
    let isEdit = ''
    cardPrint();
    submit.addEventListener("click", todoHandler);
    //this is for the todo
    function todoHandler() {
      if (!msg.value) {
        alert("you must have to give text");
      } else {
        if (isEdit) {
          let newArr=  gArr.map((item)=>{
              if(item.id==isEdit.id)
              {
                 let obj={id:item.id,text:msg.value}
                 return obj
              }
              else{
                return item
              }
            })
           gArr=newArr
           isEdit=''
           submit.innerText="ADD"
        }
        else {
          let obj = {
            id: Math.trunc(Math.random() * 10000),
            text: msg.value,
          };
          gArr.unshift(obj);
        }

        cardPrint();
      }
      msg.value = "";
    }
    //this is for delete
    function deleteHandler(id) {
      gArr = gArr.filter((item) => {
        return item.id != id
      })
      cardPrint()
    }
    //this is for the edit
    function editHandler(id) {
      let findData = gArr.find((item) => {
        return item.id == id
      })
      isEdit = findData;
      msg.value = findData.text
      submit.innerText = "UPDATE"


    }

    //this function is for printing the card
    function cardPrint() {
      let template = "";
      let body = document.getElementById("body");
      let count = document.getElementById('count')
      let todoLength = gArr.length
      if (gArr.length == 0) {
        template += '<h4 style="text-align:center">No Data</h4>';
      } else {


        gArr.forEach((item) => {
          console.log("testing", item);
          template += `    <div class="col-md-3 m-3" >
                 <div class="card bg-dark text-white">
            <div class="card-body">
              <p>${item.text}</p>
            </div>
            <div class="card-footer">
              <div class="d-flex justify-content-between">
                <button class="btn btn-primary" onclick="editHandler(${item.id})">edit</button>
                <button class="btn btn-danger" onclick="deleteHandler(${item.id})">delete</button>
              </div>
            </div>
          </div>
        </div>`;
        });

      }

      body.innerHTML = template;
      count.innerText = todoLength
    }
    //this functionality for clear all the todo
    clear.addEventListener('click', () => {
      gArr = []
      cardPrint()
    })

  </script>
</body>

</html>
