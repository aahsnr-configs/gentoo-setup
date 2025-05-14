Okay, let's enhance the previous configuration. I'll build upon the solid foundation we established, adding more features and refinements for an even better scientific writing experience in Doom Emacs with Org mode.

I'll clearly mark new additions or significant modifications with `;;;; Enhancement: ...` comments.

**Refresher on Prerequisites (Assumed from previous response):**
* Doom Emacs modules (`org`, `latex +tectonic`, `ivy +icons` or `helm`, `pdf`, `doom-themes`, `ligatures +extra`) correctly set up in `init.el`.
* Relevant packages (`org-modern`, `org-super-agenda`, `org-roam`, `org-noter`, `org-fancy-priorities`, `org-download`, `org-fragtog`, `org-roam-ui`, `org-roam-bib`, `counsel-bibtex` or `helm-bibtex`) declared in `packages.el` and installed via `doom sync`.
* JetBrains Mono Nerd Font installed system-wide.
* Tectonic installed and in PATH.
* Zotero & Better BibTeX configured for auto-exporting `.bib` files.

```elisp
;; ~/.doom.d/config.el
;; -*- lexical-binding: t; -*-

;;;; Basic Org Setup
;; Set the main directory for Org files
(setq org-directory (file-truename "~/org/"))
(setq org-agenda-files (list org-directory)) ; Point agenda to this directory
(setq org-default-notes-file (concat org-directory "notes.org")) ; A default file for quick notes
(setq org-archive-location (concat org-directory "archive/%s::")) ; Store archived tasks here

;; All org files start in overview mode
(setq org-startup-folded t)

;;;; Enhancement: Visual Indentation and Cleanliness
(setq org-startup-indented t) ; Enable org-indent-mode for visual indentation of headlines
(setq org-hide-leading-stars t) ; Hide leading stars for a cleaner look (often handled by org-modern too)
(setq org-pretty-entities t) ; Display entities like \alpha as α

;;;; Font and Headline Configuration
(defun my-org-setup-faces ()
  "Set up custom Org headline faces using JetBrains Mono Nerd Font."
  (let ((default-font "JetBrainsMono Nerd Font")
        (headline-font "JetBrainsMono Nerd Font Mono") ; Or just "JetBrainsMono Nerd Font"
        (headline-bold-font "JetBrainsMono Nerd Font Mono Bold")) ; Or "JetBrainsMono Nerd Font Bold"
    (custom-set-faces
     `(org-level-1 ((t (:inherit default :family ,headline-font :weight bold :height 1.5 :foreground ,(doom-color 'blue)))))
     `(org-level-2 ((t (:inherit default :family ,headline-font :weight bold :height 1.4 :foreground ,(doom-color 'magenta)))))
     `(org-level-3 ((t (:inherit default :family ,headline-font :weight bold :height 1.3 :foreground ,(doom-color 'cyan)))))
     `(org-level-4 ((t (:inherit default :family ,headline-font :weight bold :height 1.2 :foreground ,(doom-color 'green)))))
     `(org-level-5 ((t (:inherit default :family ,headline-font :weight bold :height 1.1 :foreground ,(doom-color 'orange)))))
     `(org-level-6 ((t (:inherit default :family ,headline-font :weight bold :height 1.0 :foreground ,(doom-color 'red)))))
     `(org-level-7 ((t (:inherit default :family ,headline-font :weight bold :height 1.0 :foreground ,(doom-color 'teal)))))
     `(org-level-8 ((t (:inherit default :family ,headline-font :weight bold :height 1.0 :foreground ,(doom-color 'yellow)))))
     `(org-document-title ((t (:inherit default :family ,headline-font :weight 'bold :height 1.6 :foreground ,(doom-color 'fg) :underline nil))))
     ;;;; Enhancement: Nicer face for org-indent to match org-modern style
     `(org-indent ((t (:inherit (org-hide fixed-pitch) :background ,(doom-color 'bg) :foreground ,(doom-blend (doom-color 'bg) (doom-color 'fg) 0.2))))))))

(add-hook 'org-mode-hook #'my-org-setup-faces)
(add-hook 'doom-load-theme-hook #'my-org-setup-faces) ; Re-apply if theme changes

;;;; Org Modern Configuration
(use-package! org-modern
  :after org
  :hook (org-mode . org-modern-mode)
  :config
  (setq org-modern-star '("●" "◉" "○" "◎"))
  (setq org-modern-table-vertical-border "│")
  (setq org-modern-table-horizontal-border "─")
  (setq org-modern-table-corner "┼")
  (setq org-modern-tag `(:face (org-tag :box (:line-width (0 . -1) :color ,(doom-color 'bg-alt)) :foreground ,(doom-color 'magenta) :weight bold :height 0.9) :icon "🏷️"))
  (setq org-modern-todo-faces t)
  (setq org-modern-priority-faces t)
  (setq org-modern-timestamp-display 'compact)
  (setq org-modern-hide-stars nil)
  (setq org-modern-list-bullet '("➤" "–" "•" "+"))
  (setq org-modern-checkbox '((?X . "☑") (?x . "☒") (?- . "⊟") (?\s . "☐") (t . "◦")))
  (setq org-modern-block-fringe nil)
  (setq org-modern-horizontal-rule "✨_.(⬤)._✨")
  (setq org-modern-footnote "[%s]")
  (setq org-modern-quote-attribution " — %s")
  (setq org-modern-link `(:face (org-modern-link :foreground ,(doom-color 'blue) :underline t) :icon "🔗 "))
  (setq org-modern-emphasis-style 'fancy)
  (setq org-modern-hide-markup t)
  ;;;; Enhancement: Org Modern Indent for cleaner headline indentation style
  (setq org-modern-indent-inner-indent nil) ; Let org-indent-mode handle this if preferred
  (setq org-modern-indent-hanging-indent t)
  (setq org-modern-indent-excluded-headline-tags '("NOINDENT"))
  (setq org-modern-indent-border `(,(doom-color 'highlight) :line-style wave)) ; Example border
  )

;; Org Ellipsis configuration
(setq org-ellipsis " ▼") ; Or try a Nerd Font icon like " "

;;;; Org TODO Keywords with Ligatures/Unicode
(setq org-todo-keywords
      '((sequence
         " TODO(t!)"  ; Pencil icon
         " NEXT(n!)"  ; Pen icon
         " INPROGRESS(i!)" ; Arrow up icon
         "🤔 WAITING(w@)" ; Thinking face
         " HOLD(h@)"    ; Hand icon
         "SOMEDAY(s!)" ; Calendar icon
         "REVIEW(r!)"  ; Magnifying glass for review
         "|"
         " DONE(d!)"  ; Checkmark icon
         " CANCELED(c@)" ; Cross mark icon
         "DELEGATED(g@)" ; Share icon
         )))

(after! org
  (setq org-todo-keyword-faces
        '(("TODO"       :inherit (org-modern-todo bold) :foreground "#fab387") ; peach
          ("NEXT"       :inherit (org-modern-todo bold) :foreground "#89b4fa") ; blue
          ("INPROGRESS" :inherit (org-modern-todo bold) :foreground "#f9e2af") ; yellow
          ("WAITING"    :inherit (org-modern-todo org-warning bold) :foreground "#f5c2e7") ; pink
          ("HOLD"       :inherit (org-modern-todo org-warning bold) :foreground "#cba6f7") ; mauve
          ("SOMEDAY"    :inherit (org-modern-todo bold) :foreground "#a6e3a1") ; green
          ("REVIEW"     :inherit (org-modern-todo bold) :foreground "#74c7ec") ; sky
          ("DONE"       :inherit (org-modern-done bold) :foreground "#89b4fa" :strike-through t) ; blue with strikethrough
          ("CANCELED"   :inherit (org-modern-cancelled bold) :foreground "#6c7086" :strike-through t) ; overlay1 with strikethrough
          ("DELEGATED"  :inherit (org-modern-todo bold) :foreground "#b4befe") ; lavender
          )))

;;;; Org Fancy Priorities
(use-package! org-fancy-priorities
  :after org
  :hook (org-mode . org-fancy-priorities-mode)
  :config
  (setq org-fancy-priorities-list '("[A] 🚨" "[B] 🔥" "[C] ⚠️" "[D] 💡" "[E] 💤"))
  (setq org-fancy-priorities-custom-faces
        `((?A :foreground ,(doom-color 'red) :weight 'bold)
          (?B :foreground ,(doom-color 'orange) :weight 'bold)
          (?C :foreground ,(doom-color 'yellow) :weight 'bold)
          (?D :foreground ,(doom-color 'blue) :weight 'bold)
          (?E :foreground ,(doom-color 'green) :weight 'bold)))
  (setq org-priority-faces org-fancy-priorities-custom-faces))

;;;; Source Code Blocks
(setq org-src-fontify-natively t)
(setq org-src-tab-acts-natively t)
(setq org-src-preserve-indentation nil)
(setq org-edit-src-content-indentation 0)
;;;; Enhancement: Easier source code block editing
(setq org-src-window-setup 'current-window) ; or 'other-window' or 'dedicated-window'
;;;; Enhancement: Auto-tangle code blocks on save
(use-package! org-auto-tangle
  :defer t
  :hook (org-mode . org-auto-tangle-mode)
  :config
  (setq org-auto-tangle-default t)) ; Tangle all files by default, or nil and set per file
;;;; Enhancement: Default Babel Languages (Example)
(after! org
  (setq org-babel-load-languages
        '((emacs-lisp . t)
          (python . t)
          (shell . t)
          (latex . t)
          (js . t)
          ;; Add other languages you frequently use
          )))
(setq org-confirm-babel-evaluate nil) ; Disable confirmation for evaluating babel blocks (use with caution)

;;;; Seamless Bold, Italic, Underline
(setq org-hide-emphasis-markers t)
;;;; Enhancement: Use org-appear for a more dynamic display of markers
(use-package! org-appear
 :after org
 :hook (org-mode . org-appear-mode)
 :config
 (setq org-appear-autoemphasis t)
 (setq org-appear-autolinks t)
 (setq org-appear-autosubmarkers t)
 (setq org-appear-autoentities t)
 (setq org-appear-trigger 'on-cursor-away) ; 'on-change or 'manual'
 (setq org-appear-delay 0.2)) ; Delay before hiding markers

;;;; Org Agenda & Super Agenda
(use-package! org-super-agenda
  :after org
  :commands org-super-agenda-mode
  :config
  (setq org-agenda-skip-deadline-if-done t)
  (setq org-agenda-skip-scheduled-if-done t)
  (setq org-agenda-skip-timestamp-if-done t)
  (setq org-agenda-start-on-weekday nil)
  ;;;; Enhancement: More agenda view options and clocking integration
  (setq org-agenda-include-deadlines t)
  (setq org-agenda-include-diary t)
  (setq org-agenda-deadline-faces '((1.001 . org-warning) (0.0 . error))) ; Sooner deadlines more prominent
  (setq org-agenda-current-time-string "ᐊ┈┈┈┈┈┈┈ Now")
  (setq org-agenda-time-grid (quote ((daily today require-timed remove-match)
                                     (800 1000 1200 1400 1600 1800 2000)
                                     "┈┈┈┈┈┈┈┈"
                                     "      %s")))
  (setq org-agenda-custom-commands
        `(("c" "Super Agenda"
           ((agenda "" ((org-agenda-span 7)
                        (org-agenda-log-mode-items '(clock)) ; Show clocked time
                        (org-agenda-entry-types '(:timestamp :sexp :deadline :scheduled))
                        (org-super-agenda-groups
                         '((:name "🔥 Today's Priorities (Due & Scheduled)"
                            :time-grid t
                            :date today
                            :deadline today
                            :scheduled today
                            :priority "A"
                            :order 1)
                           (:name "🚀 Today's Tasks"
                            :time-grid t
                            :date today
                            :todo ("INPROGRESS" "NEXT" "TODO")
                            :order 2)
                           (:name "📆 Upcoming Deadlines"
                            :deadline future
                            :order 3)
                           (:name "💡 Active Projects & Reviews"
                            :tag ("project" "research")
                            :todo ("REVIEW" "INPROGRESS" "NEXT")
                            :order 4)
                           (:name "🕰️ Waiting / On Hold"
                            :todo ("WAITING" "HOLD")
                            :order 10)
                           (:name "❗ Overdue"
                            :deadline past
                            :todo ("TODO" "NEXT" "INPROGRESS" "REVIEW")
                            :order 6)
                           (:name "💤 Someday & Delegated"
                            :todo ("SOMEDAY" "DELEGATED")
                            :order 15)
                           (:discard (:tag ("habit" "routine") :todo ("DONE" "CANCELED")))))))
            (alltodo "" ((org-agenda-sorting-strategy '(todo-state-down priority-down tag-up))
                         (org-super-agenda-groups
                          '((:name "Important Todos"
                             :priority>= "B"
                             :todo ("TODO" "NEXT" "INPROGRESS" "REVIEW")
                             :order 1)
                            (:name "Project Tasks"
                             :tag "project"
                             :todo ("TODO" "NEXT" "INPROGRESS" "REVIEW")
                             :order 2)
                            (:name "Research Tasks"
                             :tag "research"
                             :todo ("TODO" "NEXT" "INPROGRESS" "REVIEW")
                             :order 3)
                            (:name "Other Todos"
                             :todo ("TODO" "NEXT" "INPROGRESS" "REVIEW")
                             :order 4)))))
            ("W" "Weekly Review"
             ((agenda "" ((org-agenda-span 7)
                          (org-agenda-start-day "+0d")
                          (org-super-agenda-groups
                           '((:name "This Week's Schedule & Deadlines"
                              :time-grid t
                              :date-range (0 . 6)  ; today to 6 days from now
                              :deadline this-week
                              :scheduled this-week
                              :order 1)
                             (:name "Completed This Week"
                              :todo "DONE"
                              :log done
                              :order 10)))))))
            ("L" "Logbook" ((agenda "" ((org-agenda-log-mode t)
                                        (org-agenda-show-log 'clock)))))))
  (org-super-agenda-mode 1))

;;;; LaTeX, Tectonic, and Reference Management (org-cite)
(after! org
  (setq org-latex-compiler "tectonic")
  (setq org-latex-pdf-process
        '("tectonic -Z shell-escape %f -o %o --synctex"
          "tectonic -Z shell-escape %f -o %o --synctex"
          "tectonic -Z shell-escape %f -o %o --synctex"))
  (setq org-cite-bibliography
        (list (concat org-directory "references/my_library.bib")
              (concat org-directory "references/project_specific.bib")))
  (setq org-latex-prefer-biblatex t)
  (setq org-cite-export-processors
        '((latex (biblatex "biber" "--mincrossrefs=999 --sortlocale=en_US --style=alphabetic-verb") ; or try other styles like "apa", "mla", "ieee"
                 (natbib "bibtex")
                 (basic "bibtex"))
          (t (csl "citeproc-hs"))))
  (setq org-latex-listings 'minted)
  (setq org-latex-minted-options '(("frame" "lines") ("fontsize" "\\scriptsize") ("breaklines") ("breakafter")))
  (setq org-latex-with-hyperref t)
  (setq org-latex-toc-levels 4)
  ;;;; Enhancement: Define common LaTeX classes and packages
  (add-to-list 'org-latex-classes
               '("my-scientific-article"
                 "\\documentclass[11pt,a4paper,twoside]{scrartcl}
                  [DEFAULT-PACKAGES]
                  [PACKAGES]
                  \\usepackage{amsmath,amssymb,amsfonts}
                  \\usepackage{graphicx} % For images
                  \\usepackage{booktabs} % For nicer tables
                  \\usepackage{microtype} % Better typography
                  \\usepackage[svgnames]{xcolor} % For colors
                  \\usepackage{hyperref} % For clickable links and ToC
                  \\hypersetup{
                    colorlinks=true, linkcolor=blue,
                    citecolor=green, urlcolor=magenta,
                    pdftitle={\\sffamily \\@title}, % Use sans-serif for PDF title
                    pdfauthor={\\sffamily \\@author},
                    pdfsubject={Scientific Article},
                    pdfkeywords={keyword1, keyword2},
                    bookmarksopen=true,
                    bookmarksnumbered=true,
                    pdflang={en}
                  }
                  \\usepackage[T1]{fontenc}
                  \\usepackage[utf8]{inputenc}
                  \\usepackage{lmodern} % Or another modern font like newtxtext,newtxmath
                  \\usepackage{geometry} % For page layout
                  \\geometry{a4paper, top=2.5cm, bottom=2.5cm, left=2.5cm, right=2.5cm, headheight=15pt}
                  \\usepackage{scrlayer-scrpage} % For headers/footers with KOMA-Script
                  \\clearpairofpagestyles
                  \\ohead{\\pagemark}
                  \\ihead{\\headmark}
                  \\setkomafont{pageheadfoot}{\\sffamily}
                  [EXTRA]"
                 ("\\section{%s}" . "\\section*{%s}")
                 ("\\subsection{%s}" . "\\subsection*{%s}")
                 ("\\subsubsection{%s}" . "\\subsubsection*{%s}")
                 ("\\paragraph{%s}" . "\\paragraph*{%s}")
                 ("\\subparagraph{%s}" . "\\subparagraph*{%s}")))

  ;; Make sure common packages are available for [DEFAULT-PACKAGES]
  (setq org-latex-default-packages-alist
        '(("AUTO" "inputenc" t)
          ("T1" "fontenc" t)
          ("" "graphicx" t)
          ("" "longtable" nil)
          ("" "wrapfig" nil)
          ("" "rotating" nil)
          ("normalem" "ulem" t)
          ("" "amsmath" t)
          ("" "amssymb" t)
          ("" "amsfonts" t)
          ("" "textcomp" t)
          ("" "marvosym" t)
          ("" "wasysym" t)
          ("" "latexsym" t)
          ("" "hyperref" nil))) ; hyperref is added specifically in the class above for more control

  ;; Add other packages you want available via [PACKAGES] placeholder
  (add-to-list 'org-latex-packages-alist '("" "siunitx" t)) ; For SI units
  (add-to-list 'org-latex-packages-alist '("" "cleveref" t)) ; For smart cross-referencing
  (add-to-list 'org-latex-packages-alist '("" "listings" t)) ; If not using minted, or for other purposes
  (add-to-list 'org-latex-packages-alist '("" "tikz" nil)) ; For TikZ graphics (can be heavy)


  (use-package! org-fragtog
    :after org
    :hook (org-mode . org-fragtog-mode)
    :config
    (setq org-fragtog-preview-scale 1.25)
    (setq org-fragtog-highlight-background nil)
    (setq org-fragtog-debug nil)
    (setq org-fragtog-heavy-duty-cleanup t)) ; More aggressive cleanup for stability

  (use-package! org-download
    :after org
    :defer t
    :config
    (setq org-download-method 'directory)
    (setq org-download-image-dir (concat org-directory "assets/images/"))
    (setq org-download-heading-lvl nil) ; No heading for downloaded files
    (setq org-download-timestamp "%Y%m%d-%H%M%S_")
    ;;;; Enhancement: Customize org-download image display width
    (setq org-image-actual-width 600) ; Adjust default display width of inline images
    ;;;; Enhancement: Keybinding for org-download
    (map! :map org-mode-map :localleader "di" #'org-download-image) ; Download image to entry
    (map! :map org-mode-map :localleader "da" #'org-download-attach))) ; Download and attach


;;;; Org Roam v2 Configuration
(use-package! org-roam
  :after org
  :hook (org-roam-mode . org-roam-mode-enable)
  :init (setq org-roam-v2-ack t)
  :config
  (setq org-roam-directory (concat org-directory "roam/"))
  (setq org-roam-db-location (concat org-roam-directory "org-roam.db"))
  (setq org-roam-node-display-template (concat "${title} " (propertize "ID: ${id}" 'face 'font-lock-comment-face) " ${tags}"))
  (setq org-roam-completion-everywhere t)
  ;;;; Enhancement: More sophisticated Roam capture templates
  (setq org-roam-capture-templates
        '(("d" "default" plain "%?"
           :if-new (file+head "${slug}.org" "#+TITLE: ${title}\n#+CREATED: %U\n#+ROAM_ALIAS:\n#+ROAM_TAGS:\n#+CATEGORY:\n\n* ${title}\n\n%?")
           :unnarrowed t)
          ("p" "project" plain "* TODO %?\n %i\n %a"
           :if-new (file+head "${slug}.org" "#+TITLE: ${title} (Project)\n#+ROAM_TAGS: project\n#+CATEGORY: Project\n\n* Project Overview: ${title}\n\n* Tasks\n\n* Notes\n\n")
           :unnarrowed t)
          ("m" "meeting" plain "* Attendees: \n* Agenda: \n* Notes: \n%?"
           :if-new (file+head "${slug}.org" "#+TITLE: Meeting: ${title} (%<%Y-%m-%d>)\n#+ROAM_TAGS: meeting\n#+CATEGORY: Meeting\n\n* Meeting: ${title}\n\n")
           :unnarrowed t)
          ("l" "literature note" plain "%?" ; For org-roam-bib, see below
           :if-new (file+head "${citekey}.org"
                              "#+TITLE: @${citekey}: ${title}\n#+ROAM_KEY: bib:${citekey}\n#+ROAM_ALIAS: ${author-or-editor} (${year})\n#+ROAM_TAGS: literature bib\n#+AUTHOR: ${author-or-editor}\n#+YEAR: ${year}\n#+FILE: ${file}\n#+URL: ${url}\n#+DOI: ${doi}\n#+CATEGORY: Literature\n\n* Summary\n\n\n* Quotes\n\n\n* My Thoughts\n\n\n* Related\n\n")
           :unnarrowed t)
          ))

  (use-package! org-roam-bib
    :after org-roam
    :hook (org-roam-mode . org-roam-bib-mode)
    :config
    ;; Use the "l" template defined in org-roam-capture-templates for bib notes
    (setq org-roam-bib-capture-template-name "l")
    (setq org-roam-bib-literate-meta-files t)
    (setq org-roam-bib-notes-path org-roam-directory)
    (setq org-roam-bib-extra-links
          '(("Open PDF" . org-roam-bib--open-pdf)
            ("Open Zotero" . org-roam-bib--open-zotero-entry)))
    (setq org-roam-bib-completion-fallback-function #'counsel-bibtex)
    ;;;; Enhancement: Ensure counsel-bibtex uses your main bib files
    (setq bibtex-completion-bibliography (mapcar #'file-truename org-cite-bibliography))
    (setq bibtex-completion-library-path (mapcar #'file-truename org-cite-bibliography)) ; Forhelm-bibtex too
    (setq bibtex-completion-notes-path org-roam-directory)
    (setq bibtex-completion-pdf-field "file")
    (setq bibtex-completion-display-formats
          '((article       . "${=has-pdf=:1}${=has-note=:1} ${year:4} ${author:36} ${title:*}")
            (inbook        . "${=has-pdf=:1}${=has-note=:1} ${year:4} ${author:36} ${title:*}")
            (incollection  . "${=has-pdf=:1}${=has-note=:1} ${year:4} ${author:36} ${title:*}")
            (inproceedings . "${=has-pdf=:1}${=has-note=:1} ${year:4} ${author:36} ${title:*}")
            (t             . "${=has-pdf=:1}${=has-note=:1} ${year:4} ${author:36} ${title:*}"))))

  ;;;; Enhancement: Org Roam Dailies configuration
  (after! org-roam
    (require 'org-roam-dailies)
    (setq org-roam-dailies-directory "daily/") ; Subdirectory within org-roam-directory
    (setq org-roam-dailies-capture-templates
          '(("d" "default" entry "* %<%H:%M> %?"
             :if-new (file+head "${slug}.org" "#+TITLE: Daily Note - %<%Y-%m-%d %A>\n#+ROAM_TAGS: daily journal\n#+CATEGORY: Daily\n\n* Today's Focus\n\n* Log\n\n* Tasks Completed\n\n* Notes & Ideas\n"))))
    (setq org-roam-dailies-title-format "%Y-%m-%d") ; How daily note titles are formatted
    (setq org-roam-dailies-alias-format "%A, %B %e %Y")) ; Alias for easier linking

  ;; Keybindings (Doom style: SPC n r ...)
  (map! :leader
        :prefix "n"
        :desc "Org Roam" "r"
        (:prefix ("r" . "roam")
         "f" #'org-roam-node-find
         "i" #'org-roam-node-insert
         "l" #'org-roam-node-list          ; List all nodes
         "g" #'org-roam-graph              ; Basic graph
         "u" #'org-roam-ui-open            ; Open advanced UI
         "s" #'org-roam-db-sync            ; Sync database
         "t" #'org-roam-tag-add
         "c" #'org-roam-capture
         "b" #'org-roam-buffer-toggle
         "B" #'org-roam-bib-add-citation
         ;; Dailies
         :prefix ("d" . "dailies")
         "t" #'org-roam-dailies-capture-today
         "y" #'org-roam-dailies-capture-yesterday
         "m" #'org-roam-dailies-capture-tomorrow
         "d" #'org-roam-dailies-find-date
         "j" #'org-roam-dailies-goto-today ; Jump to today's note
         "p" #'org-roam-dailies-goto-previous-note
         "n" #'org-roam-dailies-goto-next-note
         ))

  (use-package! org-roam-ui
    :after org-roam
    :config
    (setq org-roam-ui-sync-theme t)
    (setq org-roam-ui-follow t)
    (setq org-roam-ui-update-on-save t)
    (setq org-roam-ui-open-on-start nil)
    (setq org-roam-ui-polling-interval 5)
    (setq org-roam-ui-port 8081)
    (setq org-roam-ui-custom-css ".org-roam-ui-graph { background-color: #1a1b26; }") ; Match Tokyo Night
    )
  (org-roam-db-autosync-mode))


;;;; Org Noter Configuration
(use-package! org-noter
  :after (org org-roam)
  :config
  (setq org-noter-notes-search-path (list org-roam-directory (concat org-directory "notes/pdf-notes/")))
  (setq org-noter-notes-window-location 'horizontal-split)
  (setq org-noter-hide-filename-extension t)
  (setq org-noter-auto-save-notes t)
  (setq org-noter-always-create-frame nil)
  (setq org-noter-default-heading-title "Page %p (%t)") ; Include time in heading

  ;;;; Enhancement: More robust Org Noter Roam integration
  (defun my-org-noter--get-roam-file-path (&optional cached-file-path force-new)
    "Create or find an Org Roam note for the current PDF.
    Stores notes in a dedicated subdirectory based on the PDF's name.
    Attempts to use citekey for naming if available via org-roam-bib."
    (let* ((doc-path (org-noter--get-doc-path))
           (file-name (file-name-nondirectory doc-path))
           (base-name (file-name-sans-extension file-name))
           (citekey (when (fboundp 'orb-get-citekeys-from-pdf)
                      (car (orb-get-citekeys-from-pdf doc-path))))
           (roam-node-title (if citekey
                                (format "@%s Notes: %s" citekey base-name)
                              (format "Notes: %s" base-name)))
           (roam-slug (if citekey
                          (org-roam-node--title-to-slug (format "%s-notes" citekey))
                        (org-roam-node--title-to-slug (format "%s-notes" base-name))))
           ;; Store noter files in a dedicated subdirectory within org-roam directory
           (roam-noter-dir (expand-file-name "noter-docs/" org-roam-directory))
           (_ (unless (file-directory-p roam-noter-dir) (make-directory roam-noter-dir t)))
           (target-file-name (expand-file-name (concat roam-slug ".org") roam-noter-dir)))

      (if (and (not force-new) (file-exists-p target-file-name))
          target-file-name
        (let ((props `(:title ,roam-node-title
                       :roam_key ,(when citekey (concat "bib:" citekey)) ; For linking to the main bib note
                       :roam_tags ,(if citekey "noter literature review" "noter pdf")
                       :noter_doc_path ,doc-path ; Store original doc path
                       :category "Noter")))
          ;; Use org-roam-capture to leverage templates and ensure node creation
          (org-roam-capture- :node (org-roam-node-create :title roam-node-title :props props :file-path target-file-name)
                             :props props
                             :templates '(("n" "noter file" plain "" :if-new (file+head "${slug}.org" "#+TITLE: ${title}\n#+ROAM_KEY: ${roam_key}\n#+ROAM_TAGS: ${roam_tags}\n#+NOTER_DOC_PATH: ${noter_doc_path}\n#+CATEGORY: ${category}\n\n* Notes for %<%Y-%m-%d>\n\n"))))
          target-file-name))))

  (setq org-noter-get-notes-file-func #'my-org-noter--get-roam-file-path)

  (map! :leader
        :prefix "n"
        :desc "Org Noter" "N"
        (:prefix ("N" . "noter")
         "s" #'org-noter
         "k" #'org-noter-kill-session
         "i" #'org-noter-insert-note
         "p" #'org-noter-insert-precise-note
         "o" #'org-noter-doc-open-file
         "e" #'org-noter-export-notes-to-pdf-document ; Export notes back to PDF
         "g" #'org-noter-sync-current-page-or-goto-current-note ; Sync PDF/Note
         )))

;;;; Theme Integration
;; Doom Tokyo Night theme should generally apply well.

;;;; Final Touches for Scientific Writing
(require 'org-id)
(setq org-export-with-toc t)
(setq org-export-with-section-numbers t)
(setq org-export-with-smart-quotes t)
(setq org-export-with-broken-links 'mark) ; Mark broken links during export
;;;; Enhancement: Auto insert Table of Contents on save if #+toc: headlines is present
(add-hook 'org-mode-hook
          (lambda ()
            (add-hook 'before-save-hook 'org-update-all-dblocks t t)))
(setq org-export-allow-bind-keywords t) ; Allow #+BIND for dynamic values in export

;;;; Enhancement: Org Tempo for faster structure insertion
(use-package! org-tempo
  :after org
  :config
  ;; org-tempo is usually enabled by default with org, provides <s TAB for src block, etc.
  ;; You can add custom tempo snippets if needed.
  (add-to-list 'org-structure-template-alist '("el" . "src emacs-lisp"))
  (add-to-list 'org-structure-template-alist '("py" . "src python"))
  (add-to-list 'org-structure-template-alist '("sh" . "src shell"))
  (add-to-list 'org-structure-template-alist '("ltx" . "src latex")))

(message "Enhanced custom Org configuration loaded successfully!")
```

**Key Enhancements and How to Use Them:**

1.  **Visuals & Editing:**
    * `org-startup-indented` and `org-hide-leading-stars` for a cleaner look.
    * `org-pretty-entities` enabled.
    * `org-indent` face tweaked to blend better with `org-modern`.
    * `org-modern-indent` configured for more styling options on headline indentation.
    * `org-appear` dynamically shows/hides emphasis markers for a smoother editing experience.
    * `org-src-window-setup` to control where source blocks are edited.
    * `org-auto-tangle-mode` automatically tangles your code blocks when you save the Org file (if they have a `:tangle yes` header or are set to tangle by default).
    * Default Babel languages pre-loaded.
    * `org-tempo` snippets added for quickly inserting common source blocks (e.g., type `<el` then `TAB` for an Emacs Lisp source block).

2.  **TODOs & Agenda:**
    * New TODO keywords: `REVIEW` and `DELEGATED`.
    * Strikethrough for `DONE` and `CANCELED` states.
    * More detailed `org-agenda-custom-commands` with priority focus, weekly review, and logbook views.
    * Agenda shows clocked time for tasks.
    * Enhanced time grid and deadline faces in the agenda.

3.  **LaTeX & Scientific Writing:**
    * A custom LaTeX class `my-scientific-article` defined with many common scientific document settings (KOMA-Script, geometry, typography, hyperref setup). You can use `#+LATEX_CLASS: my-scientific-article` at the top of your Org files.
    * `org-latex-default-packages-alist` and `org-latex-packages-alist` configured to include more useful packages like `siunitx` and `cleveref`.
    * More aggressive cleanup for `org-fragtog` for potentially better stability.
    * `org-download` keybindings (`SPC l d i` for image, `SPC l d a` for attachment).
    * `org-image-actual-width` set for a default inline image display width.

4.  **Org Roam v2:**
    * More detailed `org-roam-capture-templates` including fields for category, aliases, and specific templates for projects, meetings, and literature notes.
    * The literature note template (`"l"`) is more comprehensive, designed for `org-roam-bib`.
    * Enhanced `org-roam-dailies` setup with its own subdirectory (`daily/`), custom template, and more keybindings for navigation (`SPC n r d ...`).
    * `bibtex-completion-bibliography` and related settings ensure `counsel-bibtex` (or your chosen backend) works seamlessly with your main bib files and Org Roam notes.
    * `org-roam-ui-custom-css` to better match the Tokyo Night theme background.

5.  **Org Noter:**
    * `org-noter-default-heading-title` includes the timestamp.
    * The `my-org-noter--get-roam-file-path` function is more robust:
        * Creates a dedicated `noter-docs/` subdirectory within your Roam directory.
        * Names noter files based on the PDF name or Zotero citekey (if available) for better organization.
        * Uses `org-roam-capture-` with a specific template for creating noter files, ensuring consistency and proper Roam properties.
    * Added more `org-noter` keybindings, including exporting notes back to the PDF (`SPC n N e`) and syncing view (`SPC n N g`).

6.  **Final Touches:**
    * Automatic update of dynamic blocks (like ToC via `#+toc: headlines`) on save.
    * `org-export-allow-bind-keywords` for more dynamic exports.

This enhanced configuration should provide a significantly more powerful and streamlined environment. Remember to explore the new keybindings and features. As always, tweak settings to perfectly match your personal workflow!
