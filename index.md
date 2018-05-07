---
layout: frontpage
title: Barton Willage
description: Barton Willage is a PhD candidate at Cornell University. 
keywords: 
---




---

<div class="container">
<h4><a name="contact"></a></h4>

    <div class="row-fluid">
        <div class="span2">
        <a href="../assets/headshot.jpg">
            <img src="../assets/headshot.jpg"
                  title="Barton Willage" alt="Barton Willage"/></a>
        </div>
        
        <div class="span5">
            Barton Willage
            <br/>PhD Candidate, Economics, Cornell University<br/>
            <div id="hide_email">
            Email: bjw94@cornell.edu<br>
        
        
        <br>I will be starting as an assistant professor of economics at Louisiana State University in Fall 2018.  <br><br>
        
        I am finishing my PhD in economics at Cornell University. Before coming to Cornell, I earned a MPA in Policy Analysis from Indiana University, a MA from the University of Chicago, and a BA from Beloit College. <br>
        
            </div>
        </div>
    </div>
</div>

<br>My research areas are primarily health economics and public economics. Generally I am interested in the economic lessons we can learn from policy variation, and particularly how government interventions impact health.<br><br>
        
<div class="navbar">
  <div class="navbar-inner">
      <ul class="nav">
          <li><a href="{{ BASE_PATH }}/assets/CV.pdf">cv</a></li>
<!--      <li><a href="https://github.com/bjwillage">GitHub</a></li> -->
          <li><a href="https://twitter.com/bartonwillage">Twitter (@BartonWillage)</a></li>
      </ul>
  </div>
</div>


Last Modified: 7 May 2018
<?php
add_action ( 'manage_posts_custom_column',	'rkv_post_columns_data',	10,	2	);
add_filter ( 'manage_edit-post_columns',	'rkv_post_columns_display'			);
function rkv_post_columns_data( $column, $post_id ) {
	switch ( $column ) {
	case 'modified':
		$m_orig		= get_post_field( 'post_modified', $post_id, 'raw' );
		$m_stamp	= strtotime( $m_orig );
		$modified	= date('n/j/y @ g:i a', $m_stamp );
	       	$modr_id	= get_post_meta( $post_id, '_edit_last', true );
	       	$auth_id	= get_post_field( 'post_author', $post_id, 'raw' );
	       	$user_id	= !empty( $modr_id ) ? $modr_id : $auth_id;
	       	$user_info	= get_userdata( $user_id );
	
	       	echo '<p class="mod-date">';
	       	echo '<em>'.$modified.'</em><br />';
	       	echo 'by <strong>'.$user_info->display_name.'<strong>';
	       	echo '</p>';
		break;
	// end all case breaks
	}
}
function rkv_post_columns_display( $columns ) {
	$columns['modified']	= 'Last Modified';
	return $columns;
}

<!-- [curriculum vitae ![CV as pdf]({{ BASE_PATH }}/pages/icons16/pdf-icon.png)]({{ BASE_PATH }}/assets/CV.pdf)<br/> -->
