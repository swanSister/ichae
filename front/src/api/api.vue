
<script>
import axios from 'axios'
let ctx = {}
export default {
  install(Vue, options){
    ctx.store = options.store
  },
  kakaoLogin:function(param){
    return axios.post(`${API_URL}/users/kakaoLogin`,param)
  },
}
</script>