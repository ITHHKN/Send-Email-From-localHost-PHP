# Send Email using Mailgun with PHP 

Send Email From Loaclhost Via Mailgun with PHP 


            $msg = 'Your Message';
	
          	$mg_api = 'Your Api Key';
            
            $mg_version = 'api.mailgun.net/v2/';
            $mg_domain = "company_email.com";

            $mg_message_url = "https://".$mg_version.$mg_domain."/messages";
            $ch = curl_init();
            curl_setopt($ch, CURLOPT_HTTPAUTH, CURLAUTH_BASIC);
            curl_setopt ($ch, CURLOPT_MAXREDIRS, 3);
            curl_setopt ($ch, CURLOPT_FOLLOWLOCATION, false);
            curl_setopt ($ch, CURLOPT_RETURNTRANSFER, 1);
            curl_setopt ($ch, CURLOPT_VERBOSE, 0);
            curl_setopt ($ch, CURLOPT_HEADER, 1);
            curl_setopt ($ch, CURLOPT_CONNECTTIMEOUT, 10);
            curl_setopt ($ch, CURLOPT_SSL_VERIFYPEER, 0);
            curl_setopt ($ch, CURLOPT_SSL_VERIFYHOST, 0);
            curl_setopt($ch, CURLOPT_USERPWD, 'api:' . $mg_api);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
            curl_setopt($ch, CURLOPT_POST, true);
            //curl_setopt($curl, CURLOPT_POSTFIELDS, $params);
            curl_setopt($ch, CURLOPT_HEADER, false);
            //curl_setopt($ch, CURLOPT_CUSTOMREQUEST, 'POST');
            curl_setopt($ch, CURLOPT_URL, $mg_message_url);
            
            curl_setopt($ch, CURLOPT_POSTFIELDS,               
                    array(  'from'      => '<from>',
                            'to'        => 'to',
                            'subject'   => 'title',
                            'text'      => 'Hi, <br/> This Email is For the Varification<br/> Click This Link To active Your Email <br/> <br/> <a href='.$base_url."/activation.php?code=".$activation.'>'.$base_url.'/activation/'.$activation.'</a>'

                        ));
                        
            $result = curl_exec($ch);
            curl_close($ch);
            $res = json_decode($result,TRUE);
    
