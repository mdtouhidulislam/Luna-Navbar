# Luna-Navbar

1st. Add HTML Markup from only-nav-markup.html

2nd. Link CSS & JS File

3rd. Initialize the Navbar with the following code:

<script>
			$(document).ready(function () {
				// Fix Class Issues
				$(".sub-pages").addClass("rd-navbar-dropdown");
				$(".dynamic_dropdown").addClass("rd-navbar-megamenu");
        
			  o = $('.rd-navbar');
				if (o.length > 0) {
					o.RDNavbar({
						stickUpClone: false,
						domAppend: true,
						stickUpOffset: 250,
						focusOnHoverTimeout: 500,
						responsive: {
							0: {
								layout: 'rd-navbar-fixed',
								stickUp: false
							},
							768: {
								layout: 'rd-navbar-static',
								stickUp: true
							},
							1200: {
								layout: 'rd-navbar-static',
								stickUp: true
							}
						},
					   callbacks: {
						  onDomAppend: function(){
							  // Sidebar Class
							  te = $('.sidebartestest');
							  if (te.length > 0) {
								  $( ".sidebar-content-box" ).append( te.html() );
							  }
							  // Mobile Dropdown
							  $(".rd-navbar-nav li").each(function( index ) {
								  if($(this).hasClass("rd-navbar-submenu")){
									  tText = $(this).children("a").text();
									  $(this).children("ul").prepend( '<li><span class="close-this-subnav">'+ tText +'</span></li>' );
									  $(this).children("div").prepend( '<span class="close-this-subnav">'+ tText +'</span>' );
									  console.log(tText);
								  }
							  });

						  },
						}
				   });
				}
				$('.rd-navbar-static .rd-navbar-search form button').on('click', function(event){
					event.preventDefault();
					if($(this).hasClass("active") && $('.rd-navbar-static .rd-navbar-search input').val()){
					   $( ".rd-navbar-static .rd-navbar-search form" ).submit();
					}else{
						$(this).addClass("active");
						$(this).closest(".rd-navbar-static .rd-navbar-search").addClass("active");
					}
				});
				$('.close-this-subnav').on('click', function(){
					$(this).closest(".rd-navbar-submenu.opened").removeClass("opened");
					console.log("Clicked!");
				});
			});
		</script>
