# driver_camera_libusb

transfer bulk => initialiser l'usb puis créer un thread spécialisé qui vient faire des bulk transfer tres rapidement, faire une queue partagé pour pusher les images si le thread est dispo sinon on ignore on retourner lire les données suivantes

transfert isochrone =>
allouer un transfer (mettre une valeur de packets iso appropriée ???)
remplir la structure de transfert
->  choisir un nombre de paquet isochrone inférieur ou égal a la taille alloué
puis regler la valeur des tailles des paquets dans les struct iso_packet_desc
Determiner la capacité de son endpoint libusb_get_max_iso_packet_size()
(cela sous entend que l'on connait la quantité de données a transmettre a chaque fois (cf camera/periph usb) et cela permet de calculer une valeur approprié pour l'allocation )
