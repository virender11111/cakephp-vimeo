# cakephp-vimeo
Vimeo implementation  with cakephp

1. Download zip files from here OR download it from Vimeo  official API libraries ( https://developer.vimeo.com/api/start ).

2. unzip file and rename it from "Vimeo"

3. put this Vimeo folder into app/Vendor folder

4.set the CLIENT_ID,CLIENT_SECRET,ACCESS_TOKEN,REDIRECT_URI and SCOPES in Appcontroller (beforeFilter function) like below

            App::import('Vendor', 'Vimeo', array('file' => 'Vimeo/src/Vimeo/Vimeo.php'));
          
            define('CLIENT_ID', 'XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX');
            define('CLIENT_SECRET', 'XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX');
            
            define('ACCESS_TOKEN', 'XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX');
            
            define('REDIRECT_URI', 'XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX');
            define('SCOPES', 'public private');

5. if scopes are multiple then you can set these with space seperate.

6.make the Vimeo class object where you want to access api like below.

$lib = new \Vimeo\Vimeo(CLIENT_ID, CLIENT_SECRET);

=========================Vimeo Videos list=================================================


   $lib = new \Vimeo\Vimeo(CLIENT_ID, CLIENT_SECRET);
   $lib->setToken(ACCESS_TOKEN);
   $response = $lib->request('/me/videos', array('per_page' => 10), 'GET');


=========================Upload video on Vimeo and Title and description =====================

        $video_url = 'url of video which you want to upload';

    	$lib = new \Vimeo\Vimeo(CLIENT_ID, CLIENT_SECRET);
    
    	$lib->setToken(ACCESS_TOKEN);
    	$response = $lib->upload($video_url, false);
    	if(isset($response) && !empty($response)){
    	$lib->request($response, array('name' => 'Test', 'description' => 'Test description'), 'PATCH');
    	}

#Find more information on vimeo officail website (https://developer.vimeo.com/api/start)

Thanks
Virender