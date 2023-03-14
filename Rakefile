# Rakefile for wtsnjp/texlive-ja
require 'rake/clean'
require 'pathname'

# basics
PKG_NAME = "texlive-ja"
REF_REV = "r66482"

# directories
REPO_ROOT = Pathname.pwd
TMP_DIR = REPO_ROOT / "tmp"
BUILD_DIR = TMP_DIR / "build"
TARGET_DIR = TMP_DIR / PKG_NAME

SVN_ROOT = Pathname(Dir.home) / "repos/tug.org/texlive"
TEXLIVE_EN = "Master/texmf-dist/doc/texlive/texlive-en"

# cleaning
CLEAN.include([
  "*.aux", "*.dvi", "*.log", "*.synctex.gz", "*.toc", "*.out", "tmp"
])
CLOBBER.include(["*.pdf", "*.zip"])

# deault
task default: :archive

desc "Build the document without the tombow"
task :build do
  # initialize the build dir
  rm_rf BUILD_DIR
  mkdir_p BUILD_DIR

  # generate the main source (without the tombow option)
  main_tex = BUILD_DIR / "#{PKG_NAME}.tex"
  sh "sed s/,tombow// #{PKG_NAME}.tex > #{main_tex}"

  # build the document
  cd BUILD_DIR
  sh "TEXINPUTS='#{BUILD_DIR}:#{REPO_ROOT}//:' llmk #{PKG_NAME}.tex"
end

desc "Create an archive for TeX Live"
task :archive => :build do
  # initialize the target
  rm_rf TARGET_DIR
  mkdir_p TARGET_DIR

  # copy files to the target dir
  pkg_contents = ["img", "#{PKG_NAME}.sty"].map{|c| REPO_ROOT / c}
  pkg_contents += ["#{PKG_NAME}.tex", "#{PKG_NAME}.pdf"].map{|c| BUILD_DIR / c}
  cp_r pkg_contents, TARGET_DIR

  # create zip archive
  cd TMP_DIR
  sh "zip -q -r #{PKG_NAME}.zip #{PKG_NAME}"
  mv "#{PKG_NAME}.zip", REPO_ROOT
end

desc "Show the diff from the last referenced texlive-en"
task :diff do
  cd SVN_ROOT
  sh "svn diff -r #{REF_REV}:HEAD #{TEXLIVE_EN}/{texlive-en.tex,tex-live.sty}"
end
