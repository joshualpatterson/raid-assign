---
layout: default
page_type: create
title: Create Raid
---

<div class="container" id="content">
  <div class="row justify-content-center">
    <div class="col-12 col-lg-8">
      <div class="card mb-5">
        <div class="card-header">
          <h2>Create Raid</h2>
        </div>
        <div class="card-body">
          <div class="row">
            <div class="col-12 mb-3">
              <div class="form-group">
                <label>Instance</label>
                <select id="raid-instance-input" class="form-control">
                  <option value="">~Select Instance~</option>
                  {% for instance in site.data.data.instances %}
                  <option value="{{ instance.id }}">{{ instance.name }} ({{ instance.abbr }})</option>
                  {% endfor %}
                </select>
                <div class="alert alert-danger" id="raid-instance-error" style="display: none;"></div>
              </div>
            </div>
            <div class="col-12 mb-3">
              <div class="form-group">
                <label>Start Time (Server Time)</label>
                <div class="input-group">
                  <span class="input-group-text"><i class="bi bi-calendar-event"></i></span>
                  <input type="datetime-local" id="raid-timestamp-input" class="form-control">
                  <div class="alert alert-danger" id="raid-timestamp-error" style="display: none;"></div>
                </div>
              </div>
            </div>
            <hr class="my-4"/>
            <div class="col-12 mb-3">
              <div class="accordion" id="import-export-accordian">
                <div class="accordion-item">
                  <h2 class="accordion-header" id="import-export-accordian-header-one">
                    <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#collapseImport" aria-controls="collapseImport">
                      <i class="bi bi-upload me-1"></i> Import
                    </button>
                  </h2>
                  <div id="collapseImport" class="accordion-collapse collapse" aria-labelledby="import-export-accordian-header-one" data-bs-parent="#import-export-accordian">
                    <div class="accordion-body">
                      <div class="form-group mb-3">
                        <p class="fst-italic text-muted">Import data from an existing raid.</p>
                        <textarea id="json-import-data" class="form-control" placeholder="Paste JSON data here."></textarea>
                      </div>
                      <div class="d-flex justify-content-center">
                        <button class="btn btn-primary" id="json-import-btn"><i class="bi bi-upload"></i> Import</button>
                      </div>
                    </div>
                  </div>
                </div>
                <div class="accordion-item">
                  <h2 class="accordion-header" id="import-export-accordian-header-two">
                    <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#collapseTwo" aria-expanded="false" aria-controls="collapseTwo">
                      <i class="bi bi-download me-1"></i> Export
                    </button>
                  </h2>
                  <div id="collapseTwo" class="accordion-collapse collapse" aria-labelledby="import-export-accordian-header-two" data-bs-parent="#import-export-accordian">
                    <div class="accordion-body">
                      <div class="accordion-body">
                        <div class="form-group">
                          <div class="json-export-errors-container" style="display: none;"></div>
                          <textarea id="json-export-data" class="form-control" readonly></textarea>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div class="accordion-item">
                  <h2 class="accordion-header" id="import-export-accordian-header-three">
                    <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#collapseThree" aria-expanded="false" aria-controls="collapseThree">
                      <i class="bi bi-github me-1"></i> Save Via Gist
                    </button>
                  </h2>
                  <div id="collapseThree" class="accordion-collapse collapse" aria-labelledby="import-export-accordian-header-three" data-bs-parent="#import-export-accordian">
                    <div class="accordion-body">
                      <div class="accordion-body">
                        <div class="row">
                          <div class="col-12">
                            <div class="form-group">
                              <div class="json-export-errors-container" style="display: none;"></div>
                              <label>GitHub Token (with <code>Gist</code> scope)</label>
                              <input type="password" id="github-token" class="form-control" placeholder="ghp_xxxxxxxx..." required>
                            </div>
                          </div>
                          <div class="col-12 mt-2">
                            <div class="alert alert-warning">Do not provide a token unless you know what you are doing and trust this site. It is a static site hosted on GitHub pages and the source code is publicly available. If you are uncertain, see the instructions below for saving manually.</div>
                          </div>
                          <div class="col-12 mt-2">
                            <div class="d-flex justify-content-center align-items-center">
                              <button class="btn btn-primary mt-2" id="save-gist-btn"><i class="bi bi-floppy me-1"></i> Save with Gist</button>
                            </div>
                          </div>
                          <div class="col-12 mt-3">
                            <div id="saved-raid-container">
                            </div>
                          </div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div class="accordion-item">
                  <h2 class="accordion-header" id="import-export-accordian-header-four">
                    <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#collapseFour" aria-expanded="false" aria-controls="collapseFour">
                      <i class="bi bi-floppy me-1"></i> Save Manually
                    </button>
                  </h2>
                  <div id="collapseFour" class="accordion-collapse collapse" aria-labelledby="import-export-accordian-header-four" data-bs-parent="#import-export-accordian">
                    <div class="accordion-body">
                      <div class="accordion-body">
                        <div class="row">
                          <div class="col-12">
                            <div class="form-group">
                              <p>If you do not want to use a GitHub token to save your raid, you can opt to create your own save file and reference it as a raid ID on this site:</p>
                              <ol type="1">
                                <li>Login or create a <a href="https://github.com/login" target="_BLANK">GitHub</a> account.</li>
                                <li>Navigate to <a href="https://gist.github.com/>" target="_BLANK">GitHub Gist.</a></li>
                                <li>Enter <code>raid.json</code> into the "Filename including extension..." field.</li>
                                <li>Copy the json data from the above <i class="bi bi-download me-1"></i> Export section and paste it into the body of the Gist.</li>
                                <li>Create a <strong>Public</strong> Gist (<strong>Important! Secret Gists will not work</strong>).</li>
                                <li>Copy the Gist ID from the URL that comes after your username <code>https://gist.github.com/{yourUserName}/{gistId}</code>.</li>
                                <li>The Gist ID will double as the Raid ID and can be accessed from the home page of this site by entering it into the relevant field.</li>
                              </ol>
                            </div>
                          </div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="col-12">
      <div class="d-flex justify-content-between align-items-center">
        <h3>Characters</h3>
        <button class="btn btn-sm btn-success" id="add-character-btn"><i class="bi bi-person-add"></i> Add Character</button>
      </div>
      <hr/>
    </div>
    <div class="col-12 row mb-5" id="characters-container"></div>
    <div class="col-12">
      <div class="d-flex justify-content-between align-items-center">
        <h3>Encounters</h3>
        <button class="btn btn-sm btn-success" id="add-encounter-btn"><i class="bi bi-shield-plus"></i> Add Encounter</button>
      </div>
      <hr/>
    </div>
    <div class="col-12 mb-5" id="encounters-container"></div>
  </div>
</div>
