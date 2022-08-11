# generate webhook through gmelius enpoint- 

var a =app.endpoints.gmelius.webhooks.getAll();
var webhookExists= false;
a.data.webhooks.forEach(function (res) {
                        if (res.model_id == "${GMELIUS_HQ_WORKSPACE_ID}") {
                          log('webhook already exists');
                          webhookExists = true;
                        }
                        });
if (!webhookExists) {
  var a = app.endpoints.gmelius.webhooks.post({
  type:"shared_folder",
  model_id: "${GMELIUS_HQ_WORKSPACE_ID}",
  description: "hq dev",
  callback_url: "https://hq.slingrs.io/dev/endpoints/gmelius",
  valid_until: 60
});
}


log(JSON.stringify(a));

#slingr
