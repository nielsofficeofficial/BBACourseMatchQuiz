# BBA QUIZ MATCH

```PHP
add_action('init', function() {

	session_start();
	
	if(isset($_GET['begin']))             { BBAQuizMatchPageURL::setURL('begin');
	} else if(isset($_GET['bba-qm-pg1'])) { BBAQuizMatchPageURL::setURL('bba-qm-pg1'); 
	} else if(isset($_GET['bba-qm-pg2'])) { BBAQuizMatchPageURL::setURL('bba-qm-pg2'); 
	} else if(isset($_GET['bba-qm-pg3'])) { BBAQuizMatchPageURL::setURL('bba-qm-pg3'); 
	} else { BBAQuizMatchPageURL::setURL('bba-qm-pg4'); }

	if(	BBAQuizMatchPageURL::URL() == true ) {	

	add_action( 'bba_qm_top_add_settings_before_parent', function() {

		BBAQMSelf::assetInstall([
			'rel'  => 'stylesheet',
			'type' => 'text/css',
			'href' =>  '/wp-content/plugins/bbacoursematchquiz/public/css/bootstrap.min.css'
		], 'style');
		BBAQMSelf::lounch();
		BBAQMSelf::assetInstall([
			'rel'  => 'stylesheet',
			'type' => 'text/css',
			'href' =>  '/wp-content/plugins/bbacoursematchquiz/public/css/bbacoursematchquiz-public.css'
		], 'style');
		BBAQMSelf::lounch();
		BBAQMSelf::assetInstall([
			'type' => 'text/javascript',
			'id'   => 'jQuery',
			'src'  =>  '/wp-content/plugins/bbacoursematchquiz/public/js/jquery-3.6.0.min.js'
		]);
		BBAQMSelf::lounch();
		BBAQMSelf::assetInstall([
			'type' => 'text/javascript',
			'id'   => 'script_id',
			'src'  =>  '/wp-content/plugins/bbacoursematchquiz/public/js/bbacoursematchquiz-public.js'
		]);
		BBAQMSelf::lounch();
	});   

	add_action( 'bba_qm_add_settings_after_child_parent', function() {

		print(BBAQMSelf::BBABranding());
			 
	 });

  }
});

```PHP
add_action('init', function() {
      
	if (class_exists('BBAQMSelection')) {     
 
		BBAQuizMatchPageURL::setURL('begin');
   
	   if(BBAQuizMatchPageURL::URL() == true ) {

		   BBAQMSelection::BBATemplate('1-col' , ['box-md' , 'bba_mq'] ); 
		   BBAQMSelection::BBAaddCol1Content([
			   
			 'target'    => 'bba_qm_begin', 
			 'redirect'  => 'http://localhost/bba/quiz-match/?bba-qm-pg1', 
			 'question'  => 'BEGIN',
			 'selection' =>  [] 
			 
		   ],'lg', function() {
   
			  $html  = '';
			  $html .= '<h3>Which BBA course is right for me?</h3>';
			  $html .= '<p>Take the quiz to be matched with your perfect lash journey!</p>';

			  return($html);
   
		   });
		   BBAQMSelection::execute();  

		}

	 } else {
	   echo "PG1 | WP Plugin: BBA Quiz Match was removed or deactivated";
	 }  

 });
```

```PHP

// bba_qm_top_add_settings_before_parent
// bba_qm_add_settings_before_child_parent
// bba_qm_add_settings_after_child_parent
// bba_qm_add_settings_after_child_row_parent

// bba_qm_add_settings_bottom_child_row_parent
// bba_qm_add_settings_bottom_child_parent
// bba_qm_add_settings_after_bottom_child_parent
// bba_qm_add_settings_after_bottom_parent

		add_action( 'bba_qm_add_settings_bottom_child_row_parent', function() {
					
			BBAQMSelection::BBAaddCol1Content([	
			  'target'    => 'bba_qm2b_form', 
			  'origin'    => 'http://localhost/bba/?begin',
			  'redirect'  => 'http://localhost/bba/?bba-qm-pg2', 
			  'question'  => "I have some experience",
			  'selection' =>  [0,1,0,3] 
	
			],'lg');
			BBAQMSelection::addColContent();
```

```

