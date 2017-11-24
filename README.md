#  mySysConfig
* install git
sudo apt-get install git

* install emacs
sudo apt-get install emacs
rm -rf ~/.emacs.d
cd ~; git clone https://github.com/redguardtoo/emacs.d.git .emacs.d
** add following code to init.el

(set-frame-parameter (selected-frame) 'alpha '(85  50))
 (add-to-list 'default-frame-alist '(alpha  (85  50)))

 (defun toggle-transparency ()
   (interactive)
   (let ((alpha (frame-parameter nil 'alpha)))
     (set-frame-parameter
      nil 'alpha
      (if (eql (cond ((numberp alpha) alpha)
                     ((numberp (cdr alpha)) (cdr alpha))
                     ;; Also handle undocumented ( ) form.
                     ((numberp (cadr alpha)) (cadr alpha)))
               100)
          '(85  50) '(100  100)))))
 (global-set-key (kbd "C-c t") 'toggle-transparency)
* install zsh/oh-my-zsh
sudo apt-get install zsh
sh -c "$(wget https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"

* install powerline fonts
git clone https://github.com/powerline/fonts.git --depth=1
cd fonts;./install.sh
cd ..;rm -rf fonts

* install google chrome
sudo wget http://www.linuxidc.com/files/repo/google-chrome.list -P /etc/apt/sources.list.d/
wget -q -O - https://dl.google.com/linux/linux_signing_key.pub  | sudo apt-key add -
sudo apt-get update

* add powerline to bash
sudo apt-get install python-pip
pip install git+git://github.com/powerline/powerline 

