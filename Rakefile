##
## Rakefile for Building Report from Rakefile
##
require 'rake/clean'

REPORT_FILE = "report.pdf"
MD_FILES = FileList["src/*.md"].exclude("README.md")
TEX_FILES = MD_FILES.ext(".tex")

CLEAN.include(TEX_FILES)
CLEAN.include("*.pdf", "*.dvi", "*.log", "*.aux")

task :default => [:dvi2pdf]
  
task :dvi2pdf => [:tex2dvi] do
  sh "dvipdfmx", REPORT_FILE.ext(".dvi")
end
  
task :tex2dvi => [:md2tex] do
  sh "platex", REPORT_FILE.ext(".tex")
  sh "platex", REPORT_FILE.ext(".tex")
end

task :md2tex => TEX_FILES

# *.md -> *.tex 変換ルール
rule ".tex" => ".md" do |t|
  sh "pandoc", "-o", t.name, t.source
end
