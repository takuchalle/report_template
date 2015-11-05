##
## Rakefile for Building Report from Rakefile
##
require 'rake/clean'

REPORT_FILE = "report.pdf"
MD_FILES = FileList["src/*.md"]
TEX_FILES = MD_FILES.ext(".tex")
PNG_FILES = FileList["img/*.png"]
EPS_FILES = PNG_FILES.ext(".eps")

CLOBBER.include("*.pdf")
CLEAN.include(TEX_FILES)
CLEAN.include(EPS_FILES)
CLEAN.include("*.dvi", "*.log", "*.aux")

task :default => [:dvi2pdf]
  
task :dvi2pdf => [:tex2dvi] do
  sh "dvipdfmx", REPORT_FILE.ext(".dvi")
end
  
task :tex2dvi => [:png2eps, :md2tex] do
  sh "platex", REPORT_FILE.ext(".tex")
  sh "platex", REPORT_FILE.ext(".tex")
end

task :md2tex => TEX_FILES

task :png2eps => EPS_FILES

# *.md -> *.tex 変換ルール
rule ".tex" => ".md" do |t|
  sh "pandoc", "-t", "latex", "-o", t.name, t.source
end

# *.png -> *.eps 変換ルール
rule ".eps" => ".png" do |t|
  sh "convert", t.source, t.name
end
