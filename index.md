![Image](https://avatars1.githubusercontent.com/u/75918395?s=460&u=54d336dbd587c42e47c63dcb684ddc8a9b94cecc&v=4)

# About me
Hello! Welcome to my homepage.

I am a postdoctoral associate in the Department of Biological Engineering at the Massachusetts Institute of Technology (MIT). I am a member of the antimalarial drug discovery team  supervised by 
[Prof. Jacquin C. Niles](https://web.mit.edu/nileslab/index.html)
, and my current research involves the use of functional genetics and high throughput chemical screening towards a quick and efficient discovery of novel antimalarial chemotypes to fight the drug resistance among malaria parasites.

I received my M.Sc. degree in Chemistry (specialization in organic chemistry), and my Ph.D. degree in Chemistry from Jadavpur University (Jadavpur, WB, India). From 2013 to 2019, I carried out my doctoral thesis work under the supervision of [Prof. (Dr.) Uday Bandyopadhyay](http://www.jcbose.ac.in/faculty-details/uday-bandyopadhyay), where I was involved in the design and synthesis of novel small molecules and their biological evaluation towards the discovery of new antimalarials.

[Linkedin](https://www.linkedin.com/in/shubhra-jyoti-saha-a48451100/)

[Orcid](https://orcid.org/my-orcid)

[Google Scholar](https://scholar.google.co.in/citations?hl=en&pli=1&user=ZfIVJZQAAAAJ)

[ResearchGate](https://www.researchgate.net/profile/Shubhra_Saha)

# Research Interests

- Validation of essential genes in the _Plasmodium_ genome
- High-throughput Screening of drug library
- Biophysical assays to establish drug-target gene interaction
- Investigate the phenotypic changes

// https://github.com/netsells/customTabBar

CustomTabBar = function(settings) {
	var tabBarItems = [];
	var	tabCurrent = 0;
	
	var resetTabs = function() {
		for(var i = 0; i < tabBarItems.length; i++) {
			// Clear all the images to make sure only
			// one is shown as selected
			tabBarItems[i].image = null;
		}
	};
	
	var assignClick = function(tabItem) {
		tabItem.addEventListener('click', function(e) {
			// Just fetching the 'i' variable from the loop
			var pos = e.source.pos;

			if (tabCurrent == pos) {
				// TODO
				// Change back to root window, like the native tab action.
    			return false;
	        }		
			
			// Switch to the tab associated with the image pressed
			settings.tabBar.tabs[pos].active = true;
			tabCurrent = pos;

			
			// Reset all the tab images
			resetTabs();
			
			// Set the current tab as selected
			tabBarItems[pos].image = settings.imagePath + settings.items[pos].selected;		
		});
	};
	
	// Create the container for our tab items
	var customTabBar = Ti.UI.createWindow({
		height: settings.height,
		bottom: 0
	});
	
	
	for(var i = 0; i < settings.items.length; i++) {
		// Go through each item and create an imageView
		tabBarItems[i] = Titanium.UI.createImageView({
			// background is the default image
			backgroundImage: settings.imagePath + settings.items[i].image,
			
			// image is the selected image
			image: settings.imagePath + settings.items[i].selected,
			width: settings.width,
			height: settings.height,
			left: settings.width * i
		});

		// Pass the item number (used later for changing tabs)
		tabBarItems[i].pos = i;
		assignClick(tabBarItems[i]);

		// Add to the container window
		customTabBar.add(tabBarItems[i]);
	}

	// Display the container and it's items
	customTabBar.open();

	// Set the first item as current :)
	resetTabs();
	tabBarItems[0].image = settings.imagePath + settings.items[0].selected;
	
	return {
		hide: function() { customTabBar.hide(); },
		show: function() { customTabBar.show(); }
	};
};
