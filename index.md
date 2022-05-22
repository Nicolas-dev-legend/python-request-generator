function generate(){
    var r_url = $("#r_url").val();
    var r_method = $("#r_method").val();
    var r_headers = $("#r_headers").val();
    var r_formdata = $("#r_formdata").val();
    var righttext = $("#righttext").val();
    var lefttext = $("#lefttext").val();
    var values = $("#values").val();

    values = parseInt(values);
    if (r_url.length == 0 || r_method.length == 0 || r_headers.length == 0) {
        $('#Modal').modal('show');
        $('#ModalTitle').text("REQ GENERATOR");
        $('#ModalMsg').text("Error: Missing fields detected.");
        playError();
        return;
    }
    playClick();
    $("#r_results").text("import requests\n");
    $("#r_results").append("url = \"r_url\"\n");
   $("#r_results").append("data = \"r_formdata\"\n");

    var r_header = r_headers.split("\n");
  $("#r_results").append("headers = []\n");
    r_header.forEach(function(value, index) {
      
        $("#r_results").append("headers[] = '"+value+"'\n");
    });

     if(r_method == "POST"){
        $("#r_results").append("requests.post(url, data=data, headers=headers)\n");
    }else{
        $("#r_results").append("requests.get(url, headers=headers)\n");
    }
   
}