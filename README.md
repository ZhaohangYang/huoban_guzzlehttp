# huoban_guzzlehttp

guzzlehttp 高版本不兼容，但是伙伴的 docker 环境只能是 PHP7.0，所以高版本的使用需要做一些处理
1./vendor/guzzlehttp/guzzle/src/ClientInterface.php
public function request($method, $uri, array $options = []);
    替换为
public function request($method, $uri = null, array $options = []);

2./vendor/guzzlehttp/guzzle/src/ClientInterface.php
if (count($this->handles) >= $this->maxHandles) {  
    替换为
if (is_array($this->handles) && count($this->handles) >= $this->maxHandles) {
