.. _reference-linux-fedora-centos-post_instalacion_fedora_gnome:

#############################
Post instalación Fedora Gnome
#############################

**Fedora 26 Workstation**

:ref:`reference-linux-fedora-centos-post_instalacion_fedora`

Gnome Settings
**************

.. code-block:: bash

    # Como usuario.

    # General
    gsettings set org.gnome.desktop.interface clock-show-date true
    gsettings set org.gnome.desktop.interface gtk-theme 'Adwaita'
    gsettings set org.gnome.desktop.screensaver lock-enabled false
    gsettings set org.gnome.desktop.session idle-delay 900
    gsettings set org.gnome.desktop.wm.preferences button-layout 'appmenu:minimize,close'

    # Gedit
    gsettings set org.gnome.gedit.preferences.editor auto-indent true
    gsettings set org.gnome.gedit.preferences.editor bracket-matching true
    gsettings set org.gnome.gedit.preferences.editor highlight-current-line true
    gsettings set org.gnome.gedit.preferences.editor insert-spaces true
    gsettings set org.gnome.gedit.preferences.editor scheme 'solarized-dark'
    gsettings set org.gnome.gedit.preferences.editor tabs-size 4
    gsettings set org.gnome.gedit.preferences.editor wrap-last-split-mode 'word'
    gsettings set org.gnome.gedit.preferences.editor wrap-mode 'none'

    # Desktop
    gsettings set org.gnome.desktop.background show-desktop-icons true
    gsettings set org.gnome.nautilus.desktop home-icon-visible true
    gsettings set org.gnome.nautilus.desktop network-icon-visible false
    gsettings set org.gnome.nautilus.desktop trash-icon-visible false
    gsettings set org.gnome.nautilus.desktop volumes-visible false

    # Extension Logo Fedora
    gsettings set org.fedorahosted.background-logo-extension logo-always-visible true
    gsettings set org.fedorahosted.background-logo-extension logo-opacity 170

    # Files
    gsettings set org.gnome.nautilus.icon-view default-zoom-level 'standard'
    gsettings set org.gnome.nautilus.list-view use-tree-view true
    gsettings set org.gnome.nautilus.preferences default-folder-viewer 'icon-view'
    gsettings set org.gtk.Settings.FileChooser sort-directories-first true

    # Fuentes
    gsettings set org.gnome.desktop.interface monospace-font-name 'Dejavu Sans Mono 11'
    gsettings set org.gnome.settings-daemon.plugins.xsettings antialiasing 'rgba'
    gsettings set org.gnome.settings-daemon.plugins.xsettings hinting 'slight'

Global Dark Theme
*****************

.. code-block:: bash

    cat >> ~/.config/gtk-3.0/settings.ini << EOF
    [Settings]
    gtk-application-prefer-dark-theme=1
    EOF

Require reloguear.

Desinstalar
***********

.. code-block:: bash

    dnf remove -y \
        evolution \
        rhythmbox \
        shotwell

Programas básicos
*****************

.. code-block:: bash

    dnf -y install \
        arc-theme \
        dconf-editor \
        geary \
        gnome-tweak-tool \
        gparted \
        gpick \
        transmission-gtk \
        dnfdragora-gui # yumex-dnf

Firewalld
*********

Poner por defecto ``zone=public`` y añadir la red local a ``trusted``

.. code-block:: bash

    firewall-cmd --set-default-zone=public
    firewall-cmd --permanent --zone=trusted --add-source=192.168.1.0/24
    firewall-cmd --reload
